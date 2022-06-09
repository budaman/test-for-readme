# Link Graph

This repository contains the code for the Link Graph project.
Link Graph is an API which manages links generation and their availability (indexability) in certain domains and languages. It enables querying for a single entry or batches based on the specified page type, domain, and other identifiers.
Link Graph responses are based on the internal settings & data contained in the Resource Locator database, but heavily rely on a HA [Redis](https://redis.io/) cluster (provided by DBA), for performance and control reasons.

**Link Graph is replacing the usage of resource locator uri lookup endpoint (which is being deprecated).** Planning to migrate the uri lookups to Link Graph? Feel free to get in touch with the Growth-platform team and ask for any support!

To get more details about supported page types, check [Supported Page Types](#supported-page-types). To add a missing page type, visit [Adding New Page Type](#adding-new-page-type).

[Link Graph v2 specification document](https://docs.google.com/document/d/1-5zedvTccbr2irYPNwvz1_2kp3qEWIBVDKEDiQ9rx3s/edit?usp=sharing)

### Architecture Diagram

![Architecture Diagram](https://i.imgur.com/VJovoas.png)

## Contributing to the project

We welcome and encourage the collaboration through pull requests. Please make sure to add a brief description of what you are aiming to change/improve and why you feel such change is needed. Always a good idea to submit tests along with the code changes. Also a JIRA ticket link to add context would not be a bad thing.

## Getting started (as a contributor)

You will need **Node 12** and **Yarn 1.21.1** to run the project correctly.

### Running the project locally

- #### Install dependencies

  Using the offline option for yarn will install without network access using the binaries that are checked into the repo, and is the quickest way to install locally.

  ```bash
  yarn install --offline
  ```

- #### Selecting environment

  You can choose between `pp-rs`, `prod-sc` and `prod-ln` by setting `NODE_ENV` environment variable and it defaults to `pp-rs`. _BE CAREFUL_ if doing writes, as pp-rs data is being used for integration tests, and prod-sc/prod-ln data is being used in production.

- #### Start the api (dev mode)
  ```bash
  yarn dev
  ```
- #### Start the api as in production
  ```bash
  yarn build
  NODE_ENV=prod-sc yarn start
  ```

### Running tests

```bash
yarn test
```

Or, to keep them running while coding:

```bash
yarn test:watch
```

To run e2e tests, you need to run the application with docker compose:

```bash
docker compose up
```

### Type checking

This project is written in [Typescript](https://www.typescriptlang.org/), and exposes the following yarn commands to do type-checking:

```bash
yarn type-check
```

Or, to keep type checking active while coding:

```bash
yarn type-check:watch
```

`type-check` is also setup to run as a pre-commit hook.

### Linting and prettier

This project uses [tslint](https://palantir.github.io/tslint/) and [prettier](https://prettier.io) to do linting and code formatting. `tslint` is also setup to run as a pre-commit hook.

Prettier is configured via the `.prettierrc` file at the root of the project. Developers are free to maintain the prettier workflow they prefer (such as prettier happening automatically on save of a file, which is what we recommend).

### Adding New Page Type

To add support for a new page type, you need to:

- Add an entry to the `PageType` enum with a name of a page type. It doesn't have to be the same as the `page` field which is being used for resloc uri lookups. In perfect scenario, it should equal the pageType which is defined in GTM tracking.
- Add a JSON page config entry, based on a strict TypeScript interface, containing fields:
  - pageType - `PageType` enum value.
  - seoPageData - object with required `seoVertical`, `seoPageType`, `seoPageSubtypes` properties. If there are more than one subtype, `getPageSubtypeQueryClause` is needed as well to be able to separate different subtypes using Postgres database metadata column.
  - hasIndexabilityCalculated - boolean value, telling if an indexability task exists, which stores the data in db and redis, identifying what pages and on what domains are indexed
  - shouldIncludeInSitemap - boolean value, telling if the page type should be included in sitemap. Can only be true, when indexability task exists.
  - hasNLUrl - boolean value, if the page type has natural language urls associated with it.
  - generateNLUrlKey (optional) - function for mapping `PageOptions` to resloc nlurl lookup key. It is only required for pages, which supports nlurls.
  - activeDomains - a schema representing which domains and which languages are supported for a given page type.
  - generateStaticPath - a function for mapping `PageOptions` to a static path for pages, which doesn't support nlurls or as a fallback for failed lookups (missing nlurls).
  - generateStaticKey (optional) - a function for mapping `PageOptions` into a JSON key expression. It is only needed for pages, which doesn't have `generateNLUrlKey` function. This key is being used for indexability and static uri storage in Redis.
  - requiredOptions - an array of strings, representing required fields in `PageOptions` object.
- Add a description with an examples to the readme of this repository (follow an existing example).

### Managing pages indexability

It is possible to manage the indexability of pages (prevent or allow the google bot to crawl them) using Link Graph. The most basic use case for this is to only index the page on certain domains or languages. You can control it ussing page settings, `activeDomains` field.

It is also possible to implement the indexability overrides for certain pages or calculate the status using a custom logic (I.E. evaluating page data). To get more details, please get in touch with the Growth-platform team.

## Getting started (as a consumer of the service)

If you are interested in consuming data from Link Graph, you can find the documentation here:

http://link-graph.pp-rs.otenv.com/documentation/

If you have any request, please be in touch via Slack (#ot-team-growth-platform) or email (growth-platform-user@opentable.com).

Team's working hours: London - Kaunas office time (9am to 6pm GMT/BST, generally).

## Manual indexability tasks re-run

Indexability tasks are run every Tuesday but if you need to re-run tasks on demand, please reach out to #ot-team-growth.

Steps to re-run all the indexability tasks:

1. Make sure that [Indexability](https://teamcity.otenv.com/project/BonsaiKitten_LinkGraph_DeployLinkGraphIndexability?mode=builds) and [Redis Fill Indexability](https://teamcity.otenv.com/project/BonsaiKitten_LinkGraph_DeployLinkGraphRedisFillIndexability?mode=builds) tasks are deployed.
1. Run Indexability tasks [pp-rs](https://teamcity.otenv.com/buildConfiguration/BonsaiKitten_LinkGraph_DeployLinkGraphIndexability_OneOffPpRsK8Run), [prod-sc](https://teamcity.otenv.com/buildConfiguration/BonsaiKitten_LinkGraph_DeployLinkGraphIndexability_OneOffProdScK8Run)
1. Run Redis Fill Indexability tasks [pp-rs](https://teamcity.otenv.com/buildConfiguration/BonsaiKitten_LinkGraph_DeployLinkGraphRedisFillIndexability_OneOffPpRsK8), [prod-sc](https://teamcity.otenv.com/buildConfiguration/BonsaiKitten_LinkGraph_DeployLinkGraphRedisFillIndexability_OneOffProdScK8), [prod-ln](https://teamcity.otenv.com/buildConfiguration/BonsaiKitten_LinkGraph_DeployLinkGraphRedisFillIndexability_OneOffProdLnK8)
1. Also, if you would like that sitemap would be updated, run sitemap re-generation task [pp-rs](https://teamcity.otenv.com/buildConfiguration/BonsaiKitten_Sitemap_DeploySitemap_OneOffPpRsK8Run), [prod-sc](https://teamcity.otenv.com/buildConfiguration/BonsaiKitten_Sitemap_DeploySitemap_OneOffProdScK8Run)

## Manual Redis entries removal

In order to manually remove entries from the Redis store do the following steps:

1. Open `Deploy Link Graph Redis Remove Entries` [TeamCity pipeline](https://teamcity.otenv.com/project/BonsaiKitten_LinkGraph_DeployLinkGraphRedisRemoveEntries?mode=builds)
2. Click the `Deploy` button for the selected environment. For example, `(02.2) Deploy to PP-RS (K8S)`
3. In the opened modal fill in configuration parameters for the task
   1. Type keys pattern you want to remove from the store in the `Keys pattern to remove` field. For example, `*:demo-pattern`
   2. Type a control value `Remove it!` in the `Type "Remove it!"` field
4. Click the `Run Build` button and wait for the task to be deployed
5. The running task could be found on the K8 dashboard for the environment selected on the `2` step
   - [CI-RS](https://k8s-central-ci-rs.otenv.com/#/search?namespace=consumer&q=link-graph-redis-remove-entries)
   - [PP-RS](https://k8s-central-pp-rs.otenv.com/#/search?namespace=consumer&q=link-graph-redis-remove-entries)
   - [PROD-LN](https://k8s-central-prod-ln.otenv.com/#/search?namespace=consumer&q=link-graph-redis-remove-entries)
   - [PROD-SC](https://k8s-central-prod-sc.otenv.com/#/search?namespace=consumer&q=link-graph-redis-remove-entries)

## Overview of the infrastructure

### Teamcity

- PR test pipeline: https://teamcity.otenv.com/project.html?projectId=BonsaiKitten_LinkGraph_TestLinkGraph&tab=projectOverview

- API deployment pipeline: https://teamcity.otenv.com/project.html?projectId=BonsaiKitten_LinkGraph_DeployLinkGraph&tab=projectOverview

- Redis cache deployment pipeline: https://teamcity.otenv.com/project.html?projectId=BonsaiKitten_LinkGraph_DeployLinkGraphRedis&tab=projectOverview

### Platform3

- CI-RS service: https://k8s-central-ci-rs.otenv.com/#/deployment/consumer/link-graph?namespace=consumer
- PP-RS service: https://k8s-central-pp-rs.otenv.com/#/deployment/consumer/link-graph?namespace=consumer
- PROD-LN service: https://k8s-central-prod-ln.otenv.com/#/deployment/consumer/link-graph?namespace=consumer
- PROD-SC service: https://k8s-central-prod-sc.otenv.com/#/deployment/consumer/link-graph?namespace=consumer

### Discovery

- CI-RS announcements: http://discovery-ci-rs.otenv.com/static/state.html?sorts[serviceType]=1&perPage=100000&queries[search]=link-graph
- PP-RS announcements: http://discovery-pp-rs.otenv.com/static/state.html?sorts[serviceType]=1&perPage=100000&queries[search]=link-graph
- PROD-LN announcements: http://discovery-prod-ln.otenv.com/static/state.html?sorts[serviceType]=1&perPage=100000&queries[search]=link-graph
- PROD-SC announcements: http://discovery-prod-sc.otenv.com/static/state.html?sorts[serviceType]=1&perPage=100000&queries[search]=link-graph

### PagerDuty rota

- https://opentable.pagerduty.com/escalation_policies/#PAKEYJS

### Kibana

- Preprod stats: http://loglov3-qa.otenv.com/goto/cae5636ae99f462def562ea574ba7fda
- Preprod errors: http://loglov3-qa.otenv.com/goto/907c09c3cbcc07deac9bc542bd87d521
- Prod stats: http://loglov3-prod.otenv.com/goto/5dfd58b9f60facf863e748f38dcef072
- Prod errors: http://loglov3-prod.otenv.com/goto/8931e806dcb2ae5ba2eadc2f9a357aa2

### Grafana (Prod)

- Link Graph API: https://dashboard.otenv.com/dashboard/db/link-graph-api?orgId=1&var-env=sc&var-endpoint=-&from=1559557635669&to=1559730435669
- Link Graph API Health: https://dashboard.otenv.com/dashboard/db/link-graph-api-health?refresh=5m&orgId=1&var-env=All&var-mesos=All&from=1559557670340&to=1559730470340
- Link Graph Redis Commands: https://dashboard.otenv.com/dashboard/db/link-graph-redis?refresh=5m&orgId=1&from=1559557697749&to=1559730497749&var-env=All&var-mesos=All
- Link Graph HA Redis pod: https://dashboard.otenv.com/dashboard/db/redis-metrics?orgId=1&var-role=linkgraph_db_redis&var-region=ln&var-node=linkgraph-db-redis-prod-ln-01&var-node=linkgraph-db-redis-prod-ln-02&var-node=linkgraph-db-redis-prod-ln-03&from=now-24h&to=now

### Supported Page Types

[See this document to see the list of supported pagtypes on link graph](docs/SUPPORTED_PAGE_TYPES.md).
