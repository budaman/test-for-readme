## Supported Page Types

#### Cuisines in Metro

Page type ENUM: `cuisine-in-metro`

Indexed: `true`

Has natural language URL: `true`

Is included in sitemap: `true`

Example page: `https://www.opentable.com/st-louis-restaurants/greek`

Example static path: `https://www.opentable.com/cuisineinmetro/48/5eca5689-19bd-41e3-bbc5-fded27cd205b`

Example lookup options:

```json
{
  "pageType": "cuisine-in-metro",
  "tld": "com",
  "metroId": "48",
  "cuisineId": "5eca5689-19bd-41e3-bbc5-fded27cd205b"
}
```

#### Cuisines Near Me

Page type ENUM: `cuisine-near-me`

Indexed: `true`

Has natural language URL: `true`

Is included in sitemap: `true`

Example page: `https://www.opentable.com/nearme/italian-restaurants-near-me`

Example static path: `https://www.opentable.com/nearme/cuisine/48e9d049-40cf-4cb9-98d9-8c47d0d58986`

Example lookup options:

```json
{
  "pageType": "cuisine-near-me",
  "tld": "com",
  "cuisineId": "48e9d049-40cf-4cb9-98d9-8c47d0d58986"
}
```

#### Diner's Choice

Page type ENUM: `diners-choice`

Indexed: `true`

Has natural language URL: `true`

Is included in sitemap: `true`

Example page: `https://www.opentable.com/best-knoxville-restaurants`

Example static path: `https://www.opentable.com/s/dinerschoice?metroid=535&regionids=1036`

Example lookup options:

```json
{
  "pageType": "diners-choice",
  "tld": "com",
  "metroId": "535",
  "macroId": "1036",
  "topicId": "Healthy"
}
```

#### Editorial List

Page type ENUM: `editorial-list`

Indexed: `true`

Has natural language URL: `true`

Is included in sitemap: `true`

Example page: `https://www.opentable.com/lists/classics-seattle`

Example static path: `https://www.opentable.com/maps/d919145d38da405a915f31a4b04977a1`

Example lookup options:

```json
{
  "pageType": "editorial-list",
  "tld": "com",
  "listId": "d919145d38da405a915f31a4b04977a1"
}
```

#### Location (start)

Page type ENUM: `location`

Indexed: `true`

Has natural language URL: `true`

Is included in sitemap: `true`

Example page: `https://www.opentable.com/lists/classic-restaurants-seattle`

Example static path: `https://www.opentable.com/start/?m=255&mn=1235`

Example lookup options:

```json
{ "pageType": "location", "tld": "com", "metro": "255", "macro": "1235" }
```

#### Home

Page type ENUM: `home`

Indexed: `true`

Has natural language URL: `false`

Is included in sitemap: `true`

Example page: `https://www.opentable.com/`

Example static path: `https://www.opentable.com/`

Example lookup options:

```json
{ "pageType": "home", "tld": "com" }
```

#### Nearby

Page type ENUM: `nearby`

Indexed: `true`

Has natural language URL: `true`

Is included in sitemap: `true`

Example page: `https://www.opentable.com/nearby/restaurants-near-me-dalton-ga`

Example static path: `https://www.opentable.com/nearby/1001`

Example lookup options:

```json
{ "pageType": "nearby", "tld": "com", "nearbyId": "1001" }
```

#### Neighborhood (start-geo)

Page type ENUM: `neighborhood`

Indexed: `true`

Has natural language URL: `true`

Is included in sitemap: `true`

Example page: `https://www.opentable.com/chicago/humboldt-park-restaurants`

Example static path: `https://www.opentable.com/start/geo?mn=11&n=1534`

Example lookup options:

```json
{
  "pageType": "neighborhood",
  "tld": "com",
  "macro": "11",
  "neighborhood": "1534"
}
```

#### Landmark

Page type ENUM: `poi-landmark`

Indexed: `true`

Has natural language URL: `true`

Is included in sitemap: `true`

Example page: `https://www.opentable.com/landmark/restaurants-near-father-pandosy-mission`

Example static path: `https://www.opentable.com/landmark/100016`

Example lookup options:

```json
{ "pageType": "poi-landmark", "tld": "com", "landmarkId": "100016" }
```

#### Promo

Page type ENUM: `promo`

Indexed: `true`

Has natural language URL: `false`

Is included in sitemap: `true`

Example page: `https://www.opentable.com/promo.aspx?m=233&pid=11314`

Example static path: `https://www.opentable.com/promo.aspx?m=233&pid=11314`

Example lookup options:

```json
{ "pageType": "promo", "tld": "com", "metroId": "233", "promoId": "11314" }
```

#### Restaurant List

Page type ENUM: `restaurant-list`

Indexed: `false`

Has natural language URL: `true`

Is included in sitemap: `false`

Example page: `https://www.opentable.com/dublin-restaurant-listings`

Example static path: `https://www.opentable.com/s?metroid=3299`

Example lookup options:

```json
{
  "pageType": "restaurant-list",
  "tld": "com",
  "metro": "3299",
  "macro": "5",
  "neighborhood": "45"
}
```

#### Restaurant List New

Page type ENUM: `restaurant-list-new`

Indexed: `false`

Has natural language URL: `true`

Is included in sitemap: `false`

Example page: `https://www.opentable.com/new-seattle-washington-restaurants`

Example static path: `https://www.opentable.com/s?metroid=4&macroid=5&sortBy=newest_arrivals`

Example lookup options:

```json
{
  "pageType": "restaurant-list-new",
  "tld": "com",
  "metroId": "4",
  "macroId": "5"
}
```

#### Restaurant List Pop

Page type ENUM: `restaurant-list-pop`

Indexed: `false`

Has natural language URL: `true`

Is included in sitemap: `false`

Example page: `https://www.opentable.com/diprogram.aspx?m=5`

Example static path: `https://www.opentable.com/s?metroid=5&onlyPopTimes=true`

Example lookup options:

```json
{ "pageType": "restaurant-list-pop", "tld": "com", "metroId": "5" }
```

#### Restaurant List Offers

Page type ENUM: `restaurant-list-offers`

Indexed: `false`

Has natural language URL: `true`

Is included in sitemap: `false`

Example page: `https://www.opentable.com/restaurant-offers.aspx?m=72`

Example static path: `https://www.opentable.com/s?metroid=4&macroid=5&onlyWithOffers=true`

Example lookup options:

```json
{
  "pageType": "restaurant-list-offers",
  "tld": "com",
  "metroId": "4",
  "macroId": "5"
}
```

#### Restaurant Profile

Page type ENUM: `restaurant-profile`

Indexed: `true`

Has natural language URL: `true`

Is included in sitemap: `true`

Example page: `https://www.opentable.com/r/mad-mole-san-francisco`

Example static path: `https://www.opentable.com/restaurant/profile/421798`

Example lookup options:

```json
{ "pageType": "restaurant-profile", "tld": "com", "rid": "421798" }
```

#### Restaurant Single (Reserve)

Page type ENUM: `restaurant-single`

Indexed: `true`

Has natural language URL: `true`

Is included in sitemap: `true`

Example page: `https://www.opentable.com/r/izi-reservations-new-york`

Example static path: `https://www.opentable.com/restaurant/profile/269959/reserve`

Example lookup options:

```json
{ "pageType": "restaurant-single", "tld": "com", "rid": "269959" }
```

#### Topic Hub

Page type ENUM: `topic-hub-list`

Indexed: `true`

Has natural language URL: `true`

Is included in sitemap: `true`

Example page: `https://www.opentable.com/lists/best-vegan-restaurants`

Example static path: `https://www.opentable.com/lists/topic/6c86751753174a1a868e6e901fb0d65b`

Example lookup options:

```json
{
  "pageType": "topic-hub-list",
  "tld": "com",
  "topicId": "6c86751753174a1a868e6e901fb0d65b"
}
```

#### Phrase

Page type ENUM: `phrase`

Indexed: `true`

Has natural language URL: `true`

Is included in sitemap: `true`

Example page: `https://www.opentable.com/features/best-kid-friendly-restaurants-san-lorenzo-ca`

Example static path: `https://www.opentable.com/phrase/1225`

Example lookup options:

```json
{ "pageType": "phrase", "tld": "com", "phraseId": "1225" }
```

#### Lolz view all

Page type ENUM: `lolz-view-all`

Indexed: `false`

Has natural language URL: `false`

Is included in sitemap: `false`

Example static path: `https://www.opentable.com/lolz-view-all/H4sIAAAAAAAAAKtWslCyUnJzDHL3V9JRMjQEchKTLQ1TjVOMTBONzE2MzJItk80tjQwNjMxSk0wMzE3NlWoBaNfyAzUAAAA=`

Example lookup options:

```json
{
  "pageType": "lolz-view-all",
  "tld": "com",
  "collectionToken": "H4sIAAAAAAAAAKtWslCyUnJzDHL3V9JRMjQEchKTLQ1TjVOMTBONzE2MzJItk80tjQwNjMxSk0wMzE3NlWoBaNfyAzUAAAA="
}
```

#### Private Dining

Page type ENUM: `private-dining`

Indexed: `true`

Has natural language URL: `false`

Is included in sitemap: `false`

Example page: `https://www.opentable.com/private-dining/?m=4`

Example static path: `https://www.opentable.com/private-dining/?m=4`

Example lookup options:

```json
{ "pageType": "private-dining", "tld": "com", "metroId": "4" }
```

#### Private Event

Page type ENUM: `private-event`

Indexed: `true`

Has natural language URL: `true`

Is included in sitemap: `true`

Example page: `https://www.opentable.com/phoenix-wedding-reception-venues`

Example static path: `https://www.opentable.com/private-dining/?m=50&mn=94&pe=4`

Example lookup options:

```json
{
  "pageType": "private-event",
  "tld": "com",
  "metroId": "50",
  "macroId": "94",
  "eventTypeId": "4"
}
```

#### Cuisine in metro links

Page type ENUM: `cuisine-in-metro-links`

Indexed: `true`

Has natural language URL: `true`

Is included in sitemap: `true`

Example page: `https://www.opentable.com/cuisines/san-francisco-restaurants`

Example static path: `https://www.opentable.com/cuisineinmetro/4`

Example lookup options:

```json
{ "pageType": "cuisine-in-metro-links", "tld": "com", "metroId": "4" }
```

#### Region

Page type ENUM: `region`

Indexed: `true`

Has natural language URL: `true`

Is included in sitemap: `true`

Example page: `https://www.opentable.com/wyoming/cities`

Example static path: `https://www.opentable.com/region/WY`

Example lookup options:

```json
{ "pageType": "region", "tld": "com", "stateId": "WY" }
```

#### Near me

Page type ENUM: `near-me`

Indexed: `true`

Has natural language URL: `false`

Is included in sitemap: `true`

Example page: `https://www.opentable.com/nearby`

Example static path: `https://www.opentable.com/nearby`

Example lookup options:

```json
{ "pageType": "near-me", "tld": "com" }
```

#### Top chef

Page type ENUM: `top-chef`

Indexed: `true`

Has natural language URL: `false`

Is included in sitemap: `true`

Example page: `https://www.opentable.com/dish-it`

Example static path: `https://www.opentable.com/dish-it`

Example lookup options:

```json
{ "pageType": "top-chef", "tld": "com" }
```

#### Top chef individual

Page type ENUM: `top-chef-individual`

Indexed: `true`

Has natural language URL: `false`

Is included in sitemap: `true`

Example page: `https://www.opentable.com/dish-it/brother-luck`

Example static path: `https://www.opentable.com/dish-it/brother-luck`

Example lookup options:

```json
{ "pageType": "top-chef-individual", "tld": "com", "chefName": "brother-luck" }
```

#### Cuisines

Page type ENUM: `cuisines`

Indexed: `true`

Has natural language URL: `false`

Is included in sitemap: `true`

Example page: `https://www.opentable.com/cuisines`

Example static path: `https://www.opentable.com/cuisines`

Example lookup options:

```json
{ "pageType": "cuisines", "tld": "com" }
```

#### All Cuisines Near me

Page type ENUM: `all-cuisines-near-me`

Indexed: `true`

Has natural language URL: `false`

Is included in sitemap: `true`

Example page: `https://www.opentable.com/nearme/all-cuisines-near-me`

Example static path: `https://www.opentable.com/nearme/all-cuisines-near-me`

Example lookup options:

```json
{ "pageType": "all-cuisines-near-me", "tld": "com" }
```

#### Delivery near me

Page type ENUM: `delivery-near-me`

Indexed: `true`

Has natural language URL: `false`

Is included in sitemap: `true`

Example page: `https://www.opentable.com/delivery`

Example static path: `https://www.opentable.com/delivery`

Example lookup options:

```json
{ "pageType": "delivery-near-me", "tld": "com" }
```

#### Delivery in Metro

Page type ENUM: `delivery-in-metro`

Indexed: `true`

Has natural language URL: `true`

Is included in sitemap: `false`

Example page: `https://www.opentable.com/delivery/london`

Example static path: `https://www.opentable.com/delivery/metro/72`

Example lookup options:

```json
{ "pageType": "delivery-in-metro", "tld": "com", "metroId": "72" }
```

#### Groceries home

Page type ENUM: `groceries-home`

Indexed: `true`

Has natural language URL: `false`

Example page: `https://www.opentable.com/groceries`

Example static path: `https://www.opentable.com/groceries`

Example lookup options:

```json
{ "pageType": "groceries-home", "tld": "com" }
```

#### Mother's Day

Page type ENUM: `mothers-day`

Indexed: `true`

Has natural language URL: `false`

Is included in sitemap: `true`

Example page: `https://www.opentable.com/mothersday`

Example static path: `https://www.opentable.com/mothersday`

Example lookup options:

```json
{ "pageType": "mothers-day", "tld": "com" }
```

#### Rewards

Page type ENUM: `rewards`

Indexed: `true`

Has natural language URL: `true`

Example page: `https://www.opentable.com/rewards`

Example static path: `https://www.opentable.com/rewards`

Example lookup options:

```json
{ "pageType": "rewards", "tld": "com" }
```

#### Open Restaurants Near Me

Page type ENUM: `open-restaurants-near-me`

Indexed: `true`

Has natural language URL: `false`

Is included in sitemap: `true`

Example page: `https://www.opentable.com/open`

Example static path: `https://www.opentable.com/open`

Example lookup options:

```json
{ "pageType": "open-restaurants-near-me", "tld": "com" }
```

#### Open Restaurants Metro

Page type ENUM: `open-restaurants-in-metro`

Indexed: `true`

Has natural language URL: `true`

Is included in sitemap: `true`

Example page: `https://www.opentable.com/open/london`

Example static path: `https://www.opentable.com/open/metro/72`

Example lookup options:

```json
{ "pageType": "open-restaurants-in-metro", "tld": "com", "metroId": "72" }
```

#### Experiences Landing Page

Page type ENUM: `experiences`

Indexed: `true`

Has natural language URL: `false`

Is included in sitemap: `true`

Example page: `https://www.opentable.com/experiences/4`

Example static path: `https://www.opentable.com/experiences/4`

Example lookup options:

```json
{ "pageType": "experiences", "tld": "com", "metroId": "4" }
```

#### Experiences Near Me Page

Page type ENUM: `experiences-near-me`

Indexed: `true`

Has natural language URL: `false`

Is included in sitemap: `true`

Example page: `https://www.opentable.com/experiences`

Example static path: `https://www.opentable.com/experiences`

Example lookup options:

```json
{ "pageType": "experiences-near-me", "tld": "com" }
```

#### London Restaurant Festival

Page type ENUM: `london-restaurant-festival`

Indexed: `true`

Has natural language URL: `false`

Is included in sitemap: `true`

Example page: `https://www.opentable.co.uk/london-restaurant-festival`

Example static path: `https://www.opentable.co.uk/london-restaurant-festival`

Example lookup options:

```json
{ "pageType": "london-restaurant-festival", "tld": "com" }
```

#### Valentines

Page type ENUM: `valentines`

Indexed: `true`

Has natural language URL: `false`

Is included in sitemap: `true`

Example page: `https://www.opentable.com/valentines`

Example static path: `https://www.opentable.com/valentines`

Example lookup options:

```json
{ "pageType": "valentines", "tld": "com" }
```

#### Stella campaign

Page type ENUM: `stella-campaign`

Indexed: `false`

Has natural language URL: `false`

Is included in sitemap: `false`

Example page: `https://www.opentable.com/StellaArtois`

Example static path: `https://www.opentable.com/StellaArtois`

Example lookup options:

```json
{ "pageType": "stella-campaign", "tld": "com" }
```

#### Seasonal event

Page type ENUM: `seasonal-event`

Indexed: `true`

Has natural language URL: `true`

Is included in sitemap: `true`

Example page: `https://www.opentable.com/events/valentines-day`

Example static path: `https://www.opentable.com/events/valentines-day`

Example lookup options:

```json
{
  "pageType": "seasonal-event",
  "tld": "com",
  "eventName": "valentines-day",
  "metroId": "4"
}
```
