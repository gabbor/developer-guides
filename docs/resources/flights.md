# Flights

The **Flights** category contains a wide array of APIs that can help you manage flights, from searching for flight options to actually booking a flight.

!!! information
    Our catalogue of [Self-Service APIs](https://developers.amadeus.com/self-service){:target="\_blank"} is currently organised by categories that are different to what you see on this page.

| APIs                                                                                                                                                          | Description                                                                             |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|
| **Flight booking** |
| [Flight Offers Search](https://developers.amadeus.com/self-service/category/air/api-doc/flight-offers-search){:target="\_blank"} | Lets you can search flights between two cities, perform multi-city searches for longer itineraries and access one-way combinable fares to offer the cheapest options possible. |
| [Flight Offers Price](https://developers.amadeus.com/self-service/category/air/api-doc/flight-offers-price){:target="\_blank"} | Confirms the availability and final price (including taxes and fees) of flights returned by the Flight Offers Search API. |
| [Flight Create Orders](https://developers.amadeus.com/self-service/category/air/api-doc/flight-create-orders){:target="\_blank"} | Provides a unique booking ID and reservation details once the reservation is completed. |
| [Flight Order Management](https://developers.amadeus.com/self-service/category/air/api-doc/flight-order-management){:target="\_blank"} | Checks the latest status of a reservation, shows post-booking modifications like ticket information or form of payment and lets you cancel reservations. |
| [Seatmap Display](https://developers.amadeus.com/self-service/category/air/api-doc/seatmap-display){:target="\_blank"} | Shows airplane cabin plan from a Flight Offer in order for the traveler to be able to choose their seat during the flight booking flow. |
| [Branded Fares Upsell](https://developers.amadeus.com/self-service/category/air/api-doc/branded-fares-upsell){:target="\_blank"} | Provides the branded fares available for a given flight, along with pricing and a fare description. |
| [Flight Price Analysis](https://developers.amadeus.com/self-service/category/air/api-doc/flight-price-analysis){:target="\_blank"} | Uses an Artificial Intelligence algorithm trained on Amadeus historical flight booking data to show how current flight prices compare to historical fares and whether the price of a flight is below or above average.  |
| [Flight Choice Prediction](https://developers.amadeus.com/self-service/category/air/api-doc/flight-choice-prediction){:target="\_blank"} | Uses Artificial Intelligence and Amadeus historical flight booking data to identify which flights in search results are most likely to be booked. |
| **Flight inspiration** |
| [Flight Inspiration Search](https://developers.amadeus.com/self-service/category/air/api-doc/flight-inspiration-search){:target="\_blank"} | Provides a list of destinations from a given city that is ordered by price and can be filtered by departure date or maximum price.                |
| [Flight Cheapest Date Search](https://developers.amadeus.com/self-service/category/air/api-doc/flight-cheapest-date-search){:target="\_blank"}          |  Provides a list of flight options with dates and prices, and allows you to order by price, departure date or duration.                  |
| [Flight Availabilities Search](https://developers.amadeus.com/self-service/category/air/api-doc/flight-availabilities-search){:target="\_blank"} | Provides a list of flights with seats for sale on a given itinerary and the quantity of seats available in different fare classes. |
| [Travel Recommendations](https://developers.amadeus.com/self-service/category/trip/api-doc/travel-recommendations){:target="\_blank"} | Uses Artificial Intelligence trained on Amadeus historical flight search data to determine which destinations are also popular among travelers with similar profiles, and provides a list of recommended destinations with name, IATA code, coordinates and similarity score. |
| **Flight schedule** |
| [On Demand Flight Status](https://developers.amadeus.com/self-service/category/air/api-doc/on-demand-flight-status){:target="\_blank"} | Provides real-time flight schedule data including up-to-date departure and arrival times, terminal and gate information, flight duration and real-time delay status. Help travelers track the live status of their flight and enjoy a stress-free trip. |
| [Flight Delay Prediction](https://developers.amadeus.com/self-service/category/air/api-doc/flight-delay-prediction){:target="\_blank"} | Provides delay probabilities for four possible delay lengths |
| **Airport** |
| [Airport & City Search](https://developers.amadeus.com/self-service/category/air/api-doc/airport-and-city-search){:target="\_blank"} | Finds airports and cities that match a specific word or a string of letters. |
| [Airport Nearest Relevant](https://developers.amadeus.com/self-service/category/air/api-doc/airport-nearest-relevant){:target="\_blank"} | Provides a list of commercial airports within a 500km (311mi) radius of a given point that are ordered by relevance, which considers their distance from the starting point and their yearly flight traffic. |
| [Airport Routes API](https://developers.amadeus.com/self-service/category/air/api-doc/airport-routes){:target="\_blank"} | Finds all destinations served by a given airport. |
| [Airport On-Time Performance](https://developers.amadeus.com/self-service/category/air/api-doc/airport-on-time-performance){:target="\_blank"} | Predicts an airport's overall performance based on the delay of all flights during a day. |
| **Airlines** |
| [Flight Check-in Links](https://developers.amadeus.com/self-service/category/air/api-doc/flight-check-in-links){:target="\_blank"} |  Simplifies the check-in process by providing direct links to the airline check-in page.                |
| [Airline Code Lookup](https://developers.amadeus.com/self-service/category/air/api-doc/airline-code-lookup){:target="\_blank"}           | Finds the name of an airline by its IATA or ICAO airline codes.                  |
| [Airline Routes](https://developers.amadeus.com/self-service/category/air/api-doc/airline-routes){:target="\_blank"} | Finds all destinations served by a given airline. |


## Search flights

### Search to get flight inspirations

The [Flight Inspiration Search API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-inspiration-search){:target="\_blank"} provides a list of destinations from a given airport that is searched by the IATA code of the origin, ordered by price and filtered by departure date, one-way/round-trip, trip duration, connecting flights or maximum price.

!!!information
    The [Flight Inspiration Search API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-inspiration-search){:target="\_blank"} uses dynamic cache data. This cache data is created daily based on the most trending options that are derived from past searches and bookings. In this way, only the most trending options are included in the response.

The only mandatory query parameter is the IATA code of the origin as in the following example request that retrieves a list of destinations from Boston:

```bash
GET https://test.api.amadeus.com/v1/shopping/flight-destinations?origin=BOS
```

The departure date is an optional parameter, which needs to be provided in the YYYY-MM-DD format:

```bash
GET https://test.api.amadeus.com/v1/shopping/flight-destinations?origin=BOS&departureDate=2022-12-12
```

If the `oneWay` parameter set to `true`, only one way flight options will be provided in the response. Alternatively, if the `oneWay` parameter set to `false`, the search results will show round-trip flights. Otherwise, both flight options will be included in the results. For example, the following request shows one-way flights out of Boston:

```bash
GET https://test.api.amadeus.com/v1/shopping/flight-destinations?origin=BOS&oneWay=true
```

One-way journeys can be optionally refined by the journey duration provided in days with the `duration` parameter:

```bash
GET https://test.api.amadeus.com/v1/shopping/flight-destinations?origin=BOS&oneWay=true&duration=2
```

The `nonStop` parameter filters the search query to direct flights only:

```bash
GET https://test.api.amadeus.com/v1/shopping/flight-destinations?origin=BOS&nonStop=true
```

If you need to cap the maximum ticket price, just specify the maximum price in decimals using the `maxPrice` parameter:

```bash
GET https://test.api.amadeus.com/v1/shopping/flight-destinations?origin=BOS&maxPrice=100
```


!!!information
    This API returns cached prices. Once a destination is chosen, use the [Flight Offers Search API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-offers-search){:target="\_blank"} to get real-time pricing and availability.

The API provides a link to the [Flight Offers Search API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-offers-search){:target="\_blank"} to search for flights once a
destination is chosen and a link to the [Flight Cheapest Date Search API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-cheapest-date-search){:target="\_blank"} to check the
cheapest dates to fly:

```json
"data": [
        {
            "type": "flight-destination",
            "origin": "BOS",
            "destination": "CHI",
            "departureDate": "2022-07-22",
            "returnDate": "2022-07-28",
            "price": {
                "total": "52.18"
            },
            "links": {
                "flightDates": "https://test.api.amadeus.com/v1/shopping/flight-dates?origin=BOS&destination=CHI&departureDate=2022-07-02,2022-12-28&oneWay=false&duration=1,15&nonStop=false&maxPrice=300&currency=USD&viewBy=DURATION",
                "flightOffers": "https://test.api.amadeus.com/v2/shopping/flight-offers?originLocationCode=BOS&destinationLocationCode=CHI&departureDate=2022-07-22&returnDate=2022-07-28&adults=1&nonStop=false&maxPrice=300&currency=USD"
            }
        }
    ]
```

#### Search for destinations for a specific duration of stay

For example, let's say a traveler wants to spend six days in a city but doesn't have a strong preference for the destination. With the [Flight Inspiration Search API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-inspiration-search){:target="\_blank"} we can recommend the traveler the cheapest destinations based on the stay duration. 

This can be done using the parameter `viewBy` which returns flight destinations by `DATE`, `DESTINATION`, `DURATION`, `WEEK`, or `COUNTRY`. In our scenario we need to pass the value `DURATION` to the parameter `viewBy`, like in the example below. Also, as input we give a duration of six days and origin Miami. The departure date will be between the 1st and 3rd of September 2021.

`GET https://test.api.amadeus.com/v1/shopping/flight-destinations?departureDate=2021-09-01,2021-09-03&duration=6&origin=MIA&viewBy=DURATION`

```json
  {
            "type": "flight-destination",
            "origin": "MIA",
            "destination": "MSP",
            "departureDate": "2021-09-01",
            "returnDate": "2021-09-07",
            "price": {
                "total": "136.79"
            },
            "links": {
                "flightDates": "https://test.api.amadeus.com/v1/shopping/flight-dates?origin=MIA&destination=MSP&departureDate=2021-09-01,2021-09-03&oneWay=false&duration=6&nonStop=false&viewBy=DURATION",
                "flightOffers": "https://test.api.amadeus.com/v2/shopping/flight-offers?originLocationCode=MIA&destinationLocationCode=MSP&departureDate=2021-09-01&returnDate=2021-09-07&adults=1&nonStop=false"
            }
        },
        {
            "type": "flight-destination",
            "origin": "MIA",
            "destination": "STT",
            "departureDate": "2021-09-02",
            "returnDate": "2021-09-08",
            "price": {
                "total": "137.36"
            },
            "links": {
                "flightDates": "https://test.api.amadeus.com/v1/shopping/flight-dates?origin=MIA&destination=STT&departureDate=2021-09-01,2021-09-03&oneWay=false&duration=6&nonStop=false&viewBy=DURATION",
                "flightOffers": "https://test.api.amadeus.com/v2/shopping/flight-offers?originLocationCode=MIA&destinationLocationCode=STT&departureDate=2021-09-02&returnDate=2021-09-08&adults=1&nonStop=false"
            }
        }
```

As you can see, all the recommendations have a duration of six days and are sorted by the lowest price. The API also provides link to the [Flight Offers Search API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-offers-search){:target="\_blank"} for each result in order to check for available flights.

### Search for cheapest flights regardless of the dates

The [Flight Cheapest Date Search API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-cheapest-date-search){:target="\_blank"} finds the cheapest dates to travel from one
city to another. The API provides a list of flight options with dates and prices,
and allows you to order by price, departure date or duration.

!!!information
    The [Flight Cheapest Date Search API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-cheapest-date-search){:target="\_blank"} uses dynamic cache data. This cache data is created daily based on the most trending options that are derived from past searches and bookings. In this way, only the most trending options are included in the response.

!!!information
    This API returns cached prices. Once the dates are chosen, use the [Flight Offers Search API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-offers-search){:target="\_blank"} to get real-time pricing and availability.


The `origin` and `destination` are the two mandatory query parameters:

```bash
GET https://test.api.amadeus.com/v1/shopping/flight-dates?origin=MAD&destination=MUC
```

We can further refine our search query by the departure dates, one-way/round-trip, trip duration, connecting flights or maximum price.

The API supports one or multiple departure dates in the query provided the dates are speficied in the ISO 8601 YYYY-MM-DD format and separated by a comma:

```bash
GET https://test.api.amadeus.com/v1/shopping/flight-dates?origin=BOS&destination=CHI&departureDate=2022-08-15,2022-08-28
```

If the `oneWay` parameter set to `true`, only one way flight options will be provided in the response. Alternatively, if the `oneWay` parameter set to `false`, the search results will show round-trip flights. Otherwise, both flight options will be included in the results. For example, the following request shows one-way flights out of Boston:

```bash
GET https://test.api.amadeus.com/v1/shopping/flight-dates?origin=BOS&oneWay=true
```

One-way journeys can be optionally refined by the journey duration provided in days with the `duration` parameter:

```bash
GET https://test.api.amadeus.com/v1/shopping/flight-dates?origin=BOS&oneWay=true&duration=2
```

The `nonStop` parameter filters the search query to direct flights only:

```bash
GET https://test.api.amadeus.com/v1/shopping/flight-dates?origin=BOS&nonStop=true
```

If you need to cap the maximum ticket price, just specify the maximum price in decimals using the `maxPrice` parameter:

```bash
GET https://test.api.amadeus.com/v1/shopping/flight-dates?origin=BOS&maxPrice=100
```

The API provides a link to the [Flight Offers Search API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-offers-search){:target="\_blank"} to search for flights once a
destination is chosen, in order to proceed with the booking flow.

### Search for best flight offers

The [Flight Offers Search API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-offers-search){:target="\_blank"} searches over 500 airlines to find the cheapest
flights for a given itinerary. The API lets you search flights between two
cities, perform multi-city searches for longer itineraries and access one-way
combinable fares to offer the cheapest options possible. For each itinerary,
the API provides a list of flight offers with prices, fare details, airline
names, baggage allowances and departure terminals.

!!!tip
    - Flight Offers Search API is the first step of Flight booking engine flow. Check the details from [Video Tutorials](https://youtube.com/playlist?list=PLBehidtj-OipMAl97bHV0pxHh9yGdOrdh){:target="\_blank"} and [Blog Tutorial](https://developers.amadeus.com/blog/tutorial-booking-engine-amadeus-flight-booking-api){:target="\_blank"}. 


!!!warning
    - Flights from low-cost carriers, American Airlines, Delta and, in some markets British Airways are unavailable.

The [Flight Offers Search API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-offers-search){:target="\_blank"}  starts the booking cycle with a search for the
best fares. The API returns a list of the cheapest flights given a city/airport
of departure, a city/airport of arrival, the number and type of passengers and
travel dates. The results are complete with airline name and fares as well as
additional information, such as bag allowance and pricing for additional baggage. 

The API comes in two flavors:

- Simple version: GET operation with few parameters but which is quicker to integrate.
- On steroids: POST operation offering the full functionalities of the API.

The minimum `GET` request has following mandatory query parameters:

* IATA code for the origin location
* IATA code for the destination location
* Departure date in the ISO 8601 YYYY-MM-DD format
* Number of adult travellers

```bash
GET https://test.api.amadus.com/v2/shopping/flight-offers?adults=1&originLocationCode=BOS&destinationLocationCode=CHI&departureDate=2022-07-22
```

Let's have a look at all the optional parameters that we can use to refine the search query. One or more of these parameters can be used in addition to the mandatory query parameters.

Return date in the ISO 8601 YYYY-MM-DD format, same as the departure date:

```bash
GET https://test.api.amadeus.com/v2/shopping/flight-offers?originLocationCode=BOS&destinationLocationCode=CHI&departureDate=2022-07-22&returnDate=2022-07-26&adults=1
```

Number of children travelling, same as the number of adults:

```bash
GET https://test.api.amadeus.com/v2/shopping/flight-offers?originLocationCode=BOS&destinationLocationCode=CHI&departureDate=2022-07-26&adults=1&children=1
```

Number of infants travelling, same as the number of adults:

```bash
GET https://test.api.amadeus.com/v2/shopping/flight-offers?originLocationCode=BOS&destinationLocationCode=CHI&departureDate=2022-07-26&adults=1&infants=1
```

Travel class, which includes economy, premium economy, business or first:

```bash
GET https://test.api.amadeus.com/v2/shopping/flight-offers?originLocationCode=BOS&destinationLocationCode=CHI&departureDate=2022-07-26&adults=1&travelClass=ECONOMY
```

We can limit the search to a specific airline by providing its IATA airline code, such as BA for the British Airways:

```bash
GET https://test.api.amadeus.com/v2/shopping/flight-offers?originLocationCode=BOS&destinationLocationCode=CHI&departureDate=2022-07-26&adults=1&includedAirlineCodes=BA
```

Alternatively, we can exclude an airline from the search in a similar way:

```bash
GET https://test.api.amadeus.com/v2/shopping/flight-offers?originLocationCode=BOS&destinationLocationCode=CHI&departureDate=2022-07-26&adults=1&excludedAirlineCodes=BA
```

The `nonStop` parameter filters the search query to direct flights only:

```bash
GET https://test.api.amadeus.com/v2/shopping/flight-offers?originLocationCode=BOS&destinationLocationCode=CHI&departureDate=2022-07-26&adults=1&nonStop=true
```

The `currencyCode` defines the currency in which we will see the offer prices:

```bash
GET https://test.api.amadeus.com/v2/shopping/flight-offers?originLocationCode=BOS&destinationLocationCode=CHI&departureDate=2022-07-26&adults=1&currencyCode=EUR
```

We can limit the maximum price to a certain amount and specify the currency as described above:

```bash
GET https://test.api.amadeus.com/v2/shopping/flight-offers?originLocationCode=BOS&destinationLocationCode=CHI&departureDate=2022-07-26&adults=1&maxPrice=500&currencyCode=EUR
```

The maximum number of results retrieved can be limited using the `max` parameter in the search query:

```bash
GET https://test.api.amadeus.com/v2/shopping/flight-offers?originLocationCode=BOS&destinationLocationCode=CHI&departureDate=2022-07-26&adults=1&max=1
```


The API returns a list of `flight-offer` objects (up to 250), including
information such as itineraries, price, pricing options, etc.

```json
"data": [
    {
      "type": "flight-offer",
      "id": "1",
      "source": "GDS",
      "instantTicketingRequired": false,
      "nonHomogeneous": false,
      "oneWay": false,
      "lastTicketingDate": "2022-07-02",
      "numberOfBookableSeats": 9,
      "itineraries": [ ],
      "price": {
        "currency": "EUR",
        "total": "22.00",
        "base": "13.00",
        "fees": [
          {
            "amount": "0.00",
            "type": "SUPPLIER"
          },
          {
            "amount": "0.00",
            "type": "TICKETING"
          }
        ],
        "grandTotal": "22.00"
      }
    }
  ]
```


The `POST` endpoint consumes JSON data in the format described below. So, instead of constructing a search query, we can specify all the required parameters in the payload and pass it onto the API in the request body. In addition to this, a `X-HTTP-Method-Override` header parameter is required.

```json
{
  "currencyCode": "USD",
  "originDestinations": [
    {
      "id": "1",
      "originLocationCode": "RIO",
      "destinationLocationCode": "MAD",
      "departureDateTimeRange": {
        "date": "2022-11-01",
        "time": "10:00:00"
      }
    },
    {
      "id": "2",
      "originLocationCode": "MAD",
      "destinationLocationCode": "RIO",
      "departureDateTimeRange": {
        "date": "2022-11-05",
        "time": "17:00:00"
      }
    }
  ],
  "travelers": [
    {
      "id": "1",
      "travelerType": "ADULT"
    },
    {
      "id": "2",
      "travelerType": "CHILD"
    }
  ],
  "sources": [
    "GDS"
  ],
  "searchCriteria": {
    "maxFlightOffers": 2,
    "flightFilters": {
      "cabinRestrictions": [
        {
          "cabin": "BUSINESS",
          "coverage": "MOST_SEGMENTS",
          "originDestinationIds": [
            "1"
          ]
        }
      ],
      "carrierRestrictions": {
        "excludedCarrierCodes": [
          "AA",
          "TP",
          "AZ"
        ]
      }
    }
  }
}
```


#### Search for flights including or excluding specific airlines 

If you want your search to return flights with only specified airlines, you can use the parameter `includedAirlineCodes` to consider specific airlines. For example, there is a traveler who wants to travel from Berlin to Athens only with Aegean Airlines (A3): 

`GET https://test.api.amadeus.com/v2/shopping/flight-offers?max=3&adults=1&includedAirlineCodes=A3&originLocationCode=BER&destinationLocationCode=ATH&departureDate=2022-12-06`

With the parameter `excludedAirlineCodes` you can ignore specific airlines. For example, there is a traveler who wants to travel from Berlin to Athens ignoring both Aegean Airlines (A3) and Iberia (IB):

`GET https://test.api.amadeus.com/v2/shopping/flight-offers?max=3&adults=1&excludedAirlineCodes=A3,IB&originLocationCode=BER&destinationLocationCode=ATH&departureDate=2021-09-06`

#### Interactive code examples

Check out this [interactive code example](../examples/live-examples.md) which provides a flight search form to help you build your app. You can easily customize it and use the Flight Offers Search API to get the cheapest flight offers.

### Search for the best flight option

The [Flight Choice Prediction API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-choice-prediction){:target="\_blank"} predicts the flight your users will choose.
Our machine-learning models have analyzed historical interactions with the
[Flight Offers Search API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-offers-search){:target="\_blank"} and can determine each flight’s probability of being
chosen. Boost conversions and create a personalized experience by filtering out
the noise and showing your users the flights which are best for them.

Here is a quick cURL example piping the [Flight Offers Search API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-offers-search){:target="\_blank"} results directly to the prediction API. Please note that a `X-HTTP-Method-Override` header parameter is required.

Let’s look at flight offers for a Madrid-New York round trip (limiting to four options for this test illustration)

```bash
curl --request GET \
     --header 'Authorization: Bearer <token>' \
     --url https://test.api.amadeus.com/v2/shopping/flight-offers\?origin\=MAD\&destination\=NYC\&departureDate\=2019-08-24\&returnDate\=2019-09-19\&adults\=1 \
| curl --request POST \
       --header 'content-type: application/json' \
       --header 'Authorization: Bearer <token>' \
       --header 'X-HTTP-Method-Override: POST' \
       --url https://test.api.amadeus.com/v2/shopping/flight-offers/prediction --data @-
```

The prediction API returns the same content as the Low Fare search with the
addition of the `choiceProbability` field for each flight offer element.

```json
 {
  "data": [
    {
      "choiceProbability": "0.9437563627430908",
      "id": "1558602440311-352021104",
      "offerItems": [...],
      "type": "flight-offer"
    },
    {
      "choiceProbability": "0.0562028823257711",
      "id": "1558602440311--1831925786",
      "offerItems": [...],
      "type": "flight-offer"
    },
    {
      "choiceProbability": "0.0000252425060482",
      "id": "1558602440311-480701674",
      "offerItems": [...],
      "type": "flight-offer"
    },
    {
      "choiceProbability": "0.0000155124250899",
      "id": "1558602440311--966634676",
      "offerItems": [...],
      "type": "flight-offer"
    }
  ],
  "dictionaries": {...}
  },
  "meta": {...}
  }
}
```

#### Search for flight offers for multiple cities

Many travelers take advantage of their international trips to visit several
destinations. Multi-city search is a functionality that lets you search for
consecutive one-way flights between multiple destinations in a single request.
The returned flights are packaged as a complete, bookable itinerary. 

To perform multi-city searches, you must use the `POST` method of the [Flight Offers Search API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-offers-search){:target="\_blank"}. The API lets you search for up to six origin and
destination city pairs.

In the following example, we’ll fly from Madrid to Paris, where we’ll spend a couple of
days, then fly to Munich for three days. Next, we’ll visit Amsterdam for two
days before finishing our journey with a return to Madrid. We'll use the
following IATA city codes: `MAD > PAR > MUC > AMS > MAD`

The request will look like this:


```bash
curl https://test.api.amadeus.com/v2/shopping/flight-offers \
-d '{ 
  "originDestinations": [ 
    { 
      "id": "1", 
      "originLocationCode": "MAD", 
      "destinationLocationCode": "PAR", 
      "departureDateTimeRange": { 
        "date": "2022-10-03" 
      } 
    }, 
    { 
      "id": "2", 
      "originLocationCode": "PAR", 
      "destinationLocationCode": "MUC", 
      "departureDateTimeRange": { 
        "date": "2022-10-05" 
      } 
    }, 
    { 
      "id": "3", 
      "originLocationCode": "MUC", 
      "destinationLocationCode": "AMS", 
      "departureDateTimeRange": { 
        "date": "2022-10-08" 
      } 
    }, 
    { 
      "id": "4", 
      "originLocationCode": "AMS", 
      "destinationLocationCode": "MAD", 
      "departureDateTimeRange": { 
        "date": "2022-10-11" 
      } 
    } 
  ], 
  "travelers": [ 
    { 
      "id": "1", 
      "travelerType": "ADULT", 
      "fareOptions": [ 
        "STANDARD" 
      ] 
    } 
  ], 
  "sources": [ 
    "GDS" 
  ], 
  "searchCriteria": { 
    "maxFlightOffers": 1 
  } 
}' 
```
#### Search using loyalty programs

The [Flight Offers Price API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-offers-price){:target="\_blank"} and the [Seatmap Display API](https://developers.amadeus.com/self-service/category/air/api-doc/seatmap-display){:target="\_blank"} both accept Frequent Flyer information so end-users can benefit from their loyalty program. When adding Frequent Flyer information, please remember that each airline policy is different, and some require additional information, such as passenger name, email or phone number to validate the account. If the validation fails, your user won’t receive their loyalty program advantages.

### Search for routes from a specific airport

The [Airport Routes API](https://developers.amadeus.com/self-service/category/air/api-doc/airport-routes){:target="\_blank"} shows all destinations from a given airport. To follow up on our previous example, let's check where we can fly to from Madrid (MAD). The options are obviously quite broad, so we can limit the maximum number of results to 10. Keep in mind that this limit will apply from the beginning of the results list in the alphabetical order of the airport IATA codes.

The request will look like this:

```bash
curl --request GET \
     --header 'Authorization: Bearer <token>' \
     --url https://test.api.amadeus.com/v1/airport/direct-destinations?departureAirportCode=MAD&max=10 \
```

So we can see the the following results:

```json
{
  "meta": {
    "count": 10,
    "links": {
      "self": "https://test.api.amadeus.com/v1/airport/direct-destinations?departureAirportCode=MAD&max=10"
    }
  },
  "data": [
    {
      "type": "location",
      "subtype": "city",
      "name": "ALBACETE",
      "iataCode": "ABC"
    },
    {
      "type": "location",
      "subtype": "city",
      "name": "LANZAROTE",
      "iataCode": "ACE"
    },
    {
      "type": "location",
      "subtype": "city",
      "name": "MALAGA",
      "iataCode": "AGP"
    },
    {
      "type": "location",
      "subtype": "city",
      "name": "ALGHERO",
      "iataCode": "AHO"
    },
    {
      "type": "location",
      "subtype": "city",
      "name": "ALICANTE",
      "iataCode": "ALC"
    },
    {
      "type": "location",
      "subtype": "city",
      "name": "ALGIERS",
      "iataCode": "ALG"
    },
    {
      "type": "location",
      "subtype": "city",
      "name": "AMMAN",
      "iataCode": "AMM"
    },
    {
      "type": "location",
      "subtype": "city",
      "name": "AMSTERDAM",
      "iataCode": "AMS"
    },
    {
      "type": "location",
      "subtype": "city",
      "name": "ASUNCION",
      "iataCode": "ASU"
    },
    {
      "type": "location",
      "subtype": "city",
      "name": "ATHENS",
      "iataCode": "ATH"
    }
  ]
}
```

### Search for routes for a specific airline

The [Airline Routes API](https://developers.amadeus.com/self-service/category/air/api-doc/airline-routes){:target="\_blank"} shows all destinations for a given airline. To follow up on our previous example, let's check what destinations the British Airways fly to. There's definitely plenty of options, so we can limit the maximum number of results to two for the sake of simplicity. Keep in mind that this limit will apply from the beginning of the results list in the alphabetical order of the city names.

The request will look like this:

```bash
curl --request GET \
     --header 'Authorization: Bearer <token>' \
     --url https://test.api.amadeus.com/v1/airline/destinations?airlineCode=BA&max=2 \
```

So we can see the the following results:

```json
{
  "data": [
    {
      "type": "location",
      "subtype": "city",
      "name": "Bangalore",
      "iataCode": "BLR"
    },
    {
      "type": "location",
      "subtype": "city",
      "name": "Paris",
      "iataCode": "PAR"
    }
  ],
  "meta": {
    "count": "2",
    "sort": "iataCode",
    "links": {
      "self": "https://test.api.amadeus.com/v1/airline/destinations?airlineCode=BA&max=2"
    }
  }
}
```

### Look up the airline ICAO code by the IATA code

If we need to know the IATA code for a particular airline but only have the airline's ICAO code, the [Airline Code Lookup API](https://developers.amadeus.com/self-service/category/air/api-doc/airline-code-lookup){:target="\_blank"} can help us out. Just specify the IATA code in the query and send out the request:

```bash
curl --request GET \
     --header 'Authorization: Bearer <token>' \
     --url https://test.api.amadeus.com/v1/reference-data/airlines?airlineCodes=BA \
```

The response is pretty straightforward:

```json
{
  "meta": {
    "count": 1,
    "links": {
      "self": "https://test.api.amadeus.com/v1/reference-data/airlines?airlineCodes=BA"
    }
  },
  "data": [
    {
      "type": "airline",
      "iataCode": "BA",
      "icaoCode": "BAW",
      "businessName": "BRITISH AIRWAYS",
      "commonName": "BRITISH A/W"
    }
  ]
}
```



### Search for flight and fare availability

With the [Flight Availabilities Search API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-availabilities-search){:target="\_blank"} you can check the flight and fare availability for any itinerary. This refers to the full inventory of fares available for an itinerary at any given time. The concept of flight availability originated in the early days of flight booking as a way for agents to check what options existed for their travelers’ itineraries.

You can build the request by passing into the body of the `POST` request an object that you can customise to your needs. An example of such object is provided in the specification of the [Flight Availabilities Search API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-availabilities-search/api-reference){:target="\_blank"}. In addition to this, a `X-HTTP-Method-Override` header parameter is required.

Here’s an example request for a one-way flight from Mad (MIA) to Atlanta (ATL) for one traveler departing on December 12, 2021: 

`POST https://test.api.amadeus.com/v1/shopping/availability/flight-availabilities`

```json
{
    "originDestinations": [
        {
            "id": "1",
            "originLocationCode": "MIA",
            "destinationLocationCode": "ATL",
            "departureDateTime": {
                "date": "2021-11-01"
            }
        }
    ],
    "travelers": [
        {
            "id": "1",
            "travelerType": "ADULT"
        }
    ],
    "sources": [
        "GDS"
    ]
}
```

The response contains a list of available flights matching our request criteria (for the sake of this example, we only show the first result). Each flight availability includes descriptive data about the flight and an `availabilityClasses` list containing the available fare classes and the number of bookable seats remaining in each fare class.

```json
"data": [
        {
            "type": "flight-availability",
            "id": "1",
            "originDestinationId": "1",
            "source": "GDS",
            "instantTicketingRequired": false,
            "paymentCardRequired": false,
            "duration": "PT1H54M",
            "segments": [
                {
                    "id": "1",
                    "numberOfStops": 0,
                    "blacklistedInEU": false,
                    "departure": {
                        "iataCode": "MIA",
                        "at": "2021-11-01T05:30:00"
                    },
                    "arrival": {
                        "iataCode": "ATL",
                        "terminal": "S",
                        "at": "2022-11-01T07:24:00"
                    },
                    "carrierCode": "DL",
                    "number": "2307",
                    "aircraft": {
                        "code": "321"
                    },
                    "operating": {},
                    "availabilityClasses": [
                        {
                            "numberOfBookableSeats": 9,
                            "class": "J"
                        },
                        {
                            "numberOfBookableSeats": 9,
                            "class": "C"
                        },
                        {
                            "numberOfBookableSeats": 9,
                            "class": "D"
                        },
                        {
                            "numberOfBookableSeats": 9,
                            "class": "I"
                        },
                        {
                            "numberOfBookableSeats": 9,
                            "class": "Z"
                        },
                        {
                            "numberOfBookableSeats": 9,
                            "class": "W"
                        },
                        {
                            "numberOfBookableSeats": 9,
                            "class": "Y"
                        },
                        {
                            "numberOfBookableSeats": 9,
                            "class": "B"
                        },
                        {
                            "numberOfBookableSeats": 9,
                            "class": "M"
                        },
                        {
                            "numberOfBookableSeats": 9,
                            "class": "H"
                        },
                        {
                            "numberOfBookableSeats": 9,
                            "class": "Q"
                        },
                        {
                            "numberOfBookableSeats": 9,
                            "class": "K"
                        },
                        {
                            "numberOfBookableSeats": 9,
                            "class": "L"
                        },
                        {
                            "numberOfBookableSeats": 9,
                            "class": "U"
                        },
                        {
                            "numberOfBookableSeats": 9,
                            "class": "T"
                        },
                        {
                            "numberOfBookableSeats": 9,
                            "class": "E"
                        }
                    ]
                }
            ]
        },
```

Note that airlines’ bookable seat counters goe up to a maximum of 9, even if more seats are available in that fare class. If there are less than 9 bookable seats available, the exact number is displayed.  

### Search branded fares

Branded fares are airfares that bundle tickets with extras, such as checked bags, seat selection, refundability or loyalty points accrual. Each airline defines and packages its own branded fares and they vary from one airline to another. Branded fares not only help build brand recognition and loyalty, but also offer travelers an attractive deal as the incremental cost of the fare is usually less than that of buying the included services à la carte.  

The [Branded Fares Upsell API](https://developers.amadeus.com/self-service/category/air/api-doc/branded-fares-upsell){:target="\_blank"} receives flight offers from the [Flight Offers Search API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-offers-search){:target="\_blank"} and returns branded fares as flight offers which can be easily passed to the next step in the booking funnel. The booking flow is the following: 

- Search for flights using the [Flight Offers Search API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-offers-search){:target="\_blank"}. 
- Find branded fare options for a selected flight using the [Branded Fares Upsell API](https://developers.amadeus.com/self-service/category/air/api-doc/branded-fares-upsell){:target="\_blank"}. 
- Confirm the fare and get the final price using the [Flight Offers Price API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-offers-price){:target="\_blank"}. 
- Book the flight using the [Flight Create Orders API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-create-orders){:target="\_blank"}. 

Let's see an example of how to search for branded fares. 

You can build the request by passing the flight-offer object from the [Flight Offers Search API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-offers-search){:target="\_blank"} into the body of the `POST` request including the mandatory `X-HTTP-Method-Override` header parameter:

```bash
POST https://test.api.amadeus.com/v1/shopping/flight-offers/upselling
```

Please not that the `X-HTTP-Method-Override` header parameter is required to make this call.


```json
{ 
  "data": { 
    "type": "flight-offers-upselling", 
    "flightOffers": [ 
      {
            "type": "flight-offer",
            "id": "1",
            "source": "GDS",
            "instantTicketingRequired": false,
            "nonHomogeneous": false,
            "oneWay": false,
            "lastTicketingDate": "2022-06-12",
            "numberOfBookableSeats": 3,
            "itineraries": [
                {
                    "duration": "PT6H10M",
                    "segments": [
                        {
                            "departure": {
                                "iataCode": "MAD",
                                "terminal": "1",
                                "at": "2022-06-22T17:40:00"
                            },
                            "arrival": {
                                "iataCode": "FCO",
                                "terminal": "1",
                                "at": "2022-06-22T20:05:00"
                            },
                            "carrierCode": "AZ",
                            "number": "63",
                            "aircraft": {
                                "code": "32S"
                            },
                            "operating": {
                                "carrierCode": "AZ"
                            },
                            "duration": "PT2H25M",
                            "id": "13",
                            "numberOfStops": 0,
                            "blacklistedInEU": false
                        },
                        {
                            "departure": {
                                "iataCode": "FCO",
                                "terminal": "1",
                                "at": "2022-06-22T21:50:00"
                            },
                            "arrival": {
                                "iataCode": "ATH",
                                "at": "2022-06-23T00:50:00"
                            },
                            "carrierCode": "AZ",
                            "number": "722",
                            "aircraft": {
                                "code": "32S"
                            },
                            "operating": {
                                "carrierCode": "AZ"
                            },
                            "duration": "PT2H",
                            "id": "14",
                            "numberOfStops": 0,
                            "blacklistedInEU": false
                        }
                    ]
                }
            ],
            "price": {
                "currency": "EUR",
                "total": "81.95",
                "base": "18.00",
                "fees": [
                    {
                        "amount": "0.00",
                        "type": "SUPPLIER"
                    },
                    {
                        "amount": "0.00",
                        "type": "TICKETING"
                    }
                ],
                "grandTotal": "81.95",
                "additionalServices": [
                    {
                        "amount": "45.00",
                        "type": "CHECKED_BAGS"
                    }
                ]
            },
            "pricingOptions": {
                "fareType": [
                    "PUBLISHED"
                ],
                "includedCheckedBagsOnly": false
            },
            "validatingAirlineCodes": [
                "AZ"
            ],
            "travelerPricings": [
                {
                    "travelerId": "1",
                    "fareOption": "STANDARD",
                    "travelerType": "ADULT",
                    "price": {
                        "currency": "EUR",
                        "total": "81.95",
                        "base": "18.00"
                    },
                    "fareDetailsBySegment": [
                        {
                            "segmentId": "13",
                            "cabin": "ECONOMY",
                            "fareBasis": "OOLGEU1",
                            "class": "O",
                            "includedCheckedBags": {
                                "quantity": 0
                            }
                        },
                        {
                            "segmentId": "14",
                            "cabin": "ECONOMY",
                            "fareBasis": "OOLGEU1",
                            "brandedFare": "ECOLIGHT",
                            "class": "O",
                            "includedCheckedBags": {
                                "quantity": 0
                            }
                        }
                    ]
                }
            ]
        } 
    ]
  } 
}  
```

The API will procide the following JSON in the response:

```json
{
	"meta": {
		"count": 5
	},
	"data": [{
				"type": "flight-offer",
				"id": "2",
				"source": "GDS",
				"instantTicketingRequired": false,
				"paymentCardRequired": false,
				"lastTicketingDate": "2022-11-30",
				"itineraries": [{
					"segments": [{
						"departure": {
							"iataCode": "MAD",
							"terminal": "2",
							"at": "2022-12-01T07:10:00"
						},
						"arrival": {
							"iataCode": "ORY",
							"at": "2022-12-01T09:05:00"
						},
						"carrierCode": "UX",
						"number": "1027",
						"aircraft": {
							"code": "333"
						},
						"operating": {
							"carrierCode": "UX"
						},
						"duration": "PT1H55M",
						"id": "7",
						"numberOfStops": 0,
						"blacklistedInEU": false
					}]
				}],
				"price": {
					"currency": "EUR",
					"total": "228.38",
					"base": "210.00",
					"fees": [{
						"amount": "0.00",
						"type": "TICKETING"
					}],
					"grandTotal": "228.38"
				},
				"pricingOptions": {
					"fareType": [
						"PUBLISHED"
					],
					"includedCheckedBagsOnly": false,
					"refundableFare": false,
					"noRestrictionFare": false,
					"noPenaltyFare": false
				},
				"validatingAirlineCodes": [
					"UX"
				],
				"travelerPricings": [{
							"travelerId": "1",
							"fareOption": "STANDARD",
							"travelerType": "ADULT",
							"price": {
								"currency": "EUR",
								"total": "228.38",
								"base": "210.00",
								"taxes": [{
										"amount": "3.27",
										"code": "QV"
									},
									{
										"amount": "0.63",
										"code": "OG"
									},
									{
										"amount": "14.48",
										"code": "JD"
									}
								]
							},
							"fareDetailsBySegment": [{
								"segmentId": "7",
								"cabin": "ECONOMY",
								"fareBasis": "KYYO5L",
								"brandedFare": "LITE",
								"class": "K",
								"includedCheckedBags": {
									"quantity": 0
								},
								"amenities": [{
										"code": "0L5",
										"description": "CARRY ON HAND BAGGAGE",
										"isChargeable": false,
										"amenityType": "BAGGAGE"
									},
									{
										"code": "0CC",
										"description": "FIRST PREPAID BAG",
										"isChargeable": true,
										"amenityType": "BAGGAGE"
									},
									{
										"code": "0GO",
										"description": "PREPAID BAG",
										"isChargeable": true,
										"amenityType": "BAGGAGE"
									},
									{
										"code": "059",
										"description": "CHANGEABLE TICKET",
										"isChargeable": true,
										"amenityType": "BRANDED_FARES"
									},
									{
										"code": "0B5",
										"description": "PRE RESERVED SEAT ASSIGNMENT",
										"isChargeable": true,
										"amenityType": "PRE_RESERVED_SEAT"
									},
									{
										"code": "0G6",
										"description": "PRIORITY BOARDING",
										"isChargeable": true,
										"amenityType": "TRAVEL_SERVICES"
									}
								]
							}],
							"dictionaries": {
								"locations": {
									"MAD": {
										"cityCode": "MAD",
										"countryCode": "ES"
									},
									"ORY": {
										"cityCode": "PAR",
										"countryCode": "FR"
									}
								}
							}
						}
```

You can also see the process step to step How to upsell with branded fares in this video tutorial from [Advanced flight booking engine series](https://www.youtube.com/playlist?list=PLBehidtj-OiqHeziKjDH04IBXdvI0eBrg). 

![type:video](https://www.youtube.com/embed/Sgi-cjWNbDg)


### Search for personalized destination recommendations

The [Travel Recommendations API](https://developers.amadeus.com/self-service/category/trip/api-doc/travel-recommendations){:target="\_blank"}  provides personalized destinations based on the traveler's location and an input destination, such as a previously searched flight destination or city of interest.

For example, for a traveler based in San Francisco who has searched for multiple flights to Barcelona, what other similar destinations the API could recommend? The API takes as input the country of the traveler and the IATA code of the city that was searched, in our case this will be US and BCN respectively. 

`GET https://test.api.amadeus.com/v1/reference-data/recommended-locations?cityCodes=BCN&travelerCountryCode=US`

The response will look like this:

```json
{
     "type": "flight-date",
     "origin": "SFO",
     "destination": "ROM",
     "departureDate": "2021-09-19",
     "returnDate": "2021-09-23",
     "price": {
         "total": "348.75"
     },
     "links": {
         "flightDestinations": "https://test.api.amadeus.com/v1/shopping/flight-destinations?origin=SFO&departureDate=2021-04-15,2021-10-11&oneWay=false&duration=1,15&nonStop=false&viewBy=DURATION",
         "flightOffers": "https://test.api.amadeus.com/v2/shopping/flight-offers?originLocationCode=SFO&destinationLocationCode=ROM&departureDate=2021-09-19&returnDate=2021-09-23&adults=1&nonStop=false"
     }
 }
```




The only required parameter for the [Travel Recommendations API](https://developers.amadeus.com/self-service/category/trip/api-doc/travel-recommendations){:target="\_blank"} is the city code. So, the API is capable of suggesting flight based on that input alone:

```bash
https://test.api.amadeus.com/v1/reference-data/recommended-locations?cityCodes=PAR
```

You can also narrow the query down by using the `destinationCountryCodes` parameter, which supports one or more IATA country codes, separated by a comma:


```bash
https://test.api.amadeus.com/v1/reference-data/recommended-locations?cityCodes=PAR&destinationCountryCodes=US
```

To expand the example of the San Francisco-based traveler searching for multiple flights to Barcelona, we can specify the destination country as well:

```bash
https://test.api.amadeus.com/v1/reference-data/recommended-locations?cityCodes=BCN&travelerCountryCode=US&destinationCountryCodes=ES
```


If you want to take it to the next level, you can call the [Flight Cheapest Date Search API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-cheapest-date-search){:target="\_blank"} to let the users know not only the recommended destinations but also what are the cheapest dates to visit any of these cities. For real-time flights, you can also call the [Flight Offers Search API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-offers-search){:target="\_blank"}. The [Travel Recommendations API](https://developers.amadeus.com/self-service/category/trip/api-doc/travel-recommendations){:target="\_blank"} has returned links to both APIs. 


### Search for recommended nearby destinations 

With the [Airport Nearest Relevant API](https://developers.amadeus.com/self-service/category/air/api-doc/airport-nearest-relevant){:target="\_blank"} you can find the closest major airports to a starting point. By default, results are sorted by relevance but they can also be sorted by `distance`, `flights`, `travelers` using the parameter `sort`.

!!!information
    To get the latitude and longitude of a city you can use the [Airport & City Search API](https://developers.amadeus.com/self-service/category/air/api-doc/airport-and-city-search){:target="\_blank"} using the city's IATA code.

Let's call the [Airport Nearest Relevant API](https://developers.amadeus.com/self-service/category/air/api-doc/airport-nearest-relevant){:target="\_blank"} to find airports within the 500km radius of Madrid.

`GET https://test.api.amadeus.com/v1/reference-data/locations/airports?latitude=40.416775&longitude=-3.703790&radius=500`

A part of the response looks like:
 
```json
        {
            "type": "location",
            "subType": "AIRPORT",
            "name": "AIRPORT",
            "detailedName": "BARCELONA/ES:AIRPORT",
            "timeZoneOffset": "+02:00",
            "iataCode": "BCN",
            "geoCode": {
                "latitude": 41.29694,
                "longitude": 2.07833
            },
            "address": {
                "cityName": "BARCELONA",
                "cityCode": "BCN",
                "countryName": "SPAIN",
                "countryCode": "ES",
                "regionCode": "EUROP"
            },
            "distance": {
                "value": 496,
                "unit": "KM"
            },
            "analytics": {
                "flights": {
                    "score": 25
                },
                "travelers": {
                    "score": 25
                }
            },
            "relevance": 5.11921
        }
```
What we want to do at this point, is to find the cheapest dates for all these destinations. 

We can do this by calling the [Flight Cheapest Date Search API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-cheapest-date-search){:target="\_blank"} which finds the cheapest dates to travel from one city to another. Let's see, for example, the cheapest dates to fly to Barcelona in November 2021. 

`GET https://test.api.amadeus.com/v1/shopping/flight-dates?origin=MAD&destination=BCN&departureDate=2021-05-01,2021-05-30`

```json
{
    "type": "flight-date",
    "origin": "MAD",
    "destination": "BCN",
    "departureDate": "2021-05-29",
    "returnDate": "2021-06-11",
    "price": {
        "total": "73.61"
    },
    "links": {
        "flightDestinations": "https://test.api.amadeus.com/v1/shopping/flight-destinations?origin=MAD&departureDate=2021-05-01,2021-05-30&oneWay=false&duration=1,15&nonStop=false&viewBy=DURATION",
        "flightOffers": "https://test.api.amadeus.com/v2/shopping/flight-offers?originLocationCode=MAD&destinationLocationCode=BCN&departureDate=2022-09-29&returnDate=2021-06-11&adults=1&nonStop=false"
    },
{
    "type": "flight-date",
    "origin": "MAD",
    "destination": "BCN",
    "departureDate": "2021-05-05",
    "returnDate": "2021-05-06",
    "price": {
        "total": "79.67"
    },
    "links": {
        "flightDestinations": "https://test.api.amadeus.com/v1/shopping/flight-destinations?origin=MAD&departureDate=2021-05-01,2021-05-30&oneWay=false&duration=1,15&nonStop=false&viewBy=DURATION",
        "flightOffers": "https://test.api.amadeus.com/v2/shopping/flight-offers?originLocationCode=MAD&destinationLocationCode=BCN&departureDate=2021-05-05&returnDate=2021-05-06&adults=1&nonStop=false"
    }
},
{
    "type": "flight-date",
    "origin": "MAD",
    "destination": "BCN",
    "departureDate": "2021-05-02",
    "returnDate": "2021-05-06",
    "price": {
        "total": "80.61"
    },
    "links": {
        "flightDestinations": "https://test.api.amadeus.com/v1/shopping/flight-destinations?origin=MAD&departureDate=2021-05-01,2021-05-30&oneWay=false&duration=1,15&nonStop=false&viewBy=DURATION",
        "flightOffers": "https://test.api.amadeus.com/v2/shopping/flight-offers?originLocationCode=MAD&destinationLocationCode=BCN&departureDate=2021-05-02&returnDate=2021-05-06&adults=1&nonStop=false"
    }
}
```
As you can see above, in the results we have a list of dates for a roundtrip from Madrid to Barcelona ordered by the lowest price.


In the last step, we want to let the traveler perform a flight search for any of the above dates that are convenient for them. That is very easy with our APIs, as the [Flight Cheapest Date Search API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-cheapest-date-search){:target="\_blank"} for each result contains a link to the [Flight Offers Search API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-offers-search){:target="\_blank"}. For example, if we want to perform a flight search for the first result, we only have to take the link provided and make an API call:


`GET https://test.api.amadeus.com/v2/shopping/flight-offers?originLocationCode=MAD&destinationLocationCode=BCN&departureDate=2021-05-29&returnDate=2021-06-11&adults=1&nonStop=false`


### Search for a city that has an airport

The [Airport & City Search API](https://developers.amadeus.com/self-service/category/air/api-doc/airport-and-city-search){:target="\_blank"} finds airports and cities that match a specific word or a string of letters. Using this API, you can automatically suggest
airports based on what the traveler enters in the search field. The API provides a list of airports/cities ordered by yearly passenger volume with the name, 3-letter IATA code, time zone and coordinates of each airport. 

!!! information
    Please keep in mind that [Airport & City Search API](https://developers.amadeus.com/self-service/category/air/api-doc/airport-and-city-search){:target="\_blank"} only returns the cities which have an airport. 
    If you want to retrieve any city that matches a search keyword, check out [City Search API](https://developers.amadeus.com/self-service/category/trip/api-doc/city-search){:target="\_blank"}.


The [Airport & City Search API](https://developers.amadeus.com/self-service/category/air/api-doc/airport-and-city-search){:target="\_blank"} has two endpoints:

You can see the process step to step in this video tutorial.

![type:video](https://www.youtube.com/embed/Fbz3LOXoDh0)


* `GET ​/reference-data​/locations` to return a list of airports and cities by a keyword
* `GET ​/reference-data​/locations//reference-data/locations/{locationId}` to return an airport or city by Id

To get a list of airports and cities by a keyword, we need to two mandatory query parameters:

* `subType` - this defines whether we are looking for an airport or a city
* `keyword` - this defines the keyword (or a part of it) used in our search, which can be any character in the range of A-Za-z0-9./:-'()"

Here is a basic query to look for any airport whose name starts with a letter M:

```bash
https://test.api.amadeus.com/v1/reference-data/locations?subType=AIRPORT&keyword=M
```

To narrow the search down, we can use an optional parameter `countryCode`, which is a location code in the ISO 3166-1 alpha-2 format:

```bash
https://test.api.amadeus.com/v1/reference-data/locations?subType=AIRPORT&keyword=M&countryCode=US
```

The [Airport & City Search API](https://developers.amadeus.com/self-service/category/air/api-doc/airport-and-city-search){:target="\_blank"} supports [pagination](../pagination.md) and dynamic sorting. The dynamic sorting enables you to sort by the results by the number of travelers by airport or city where the airports and cities with the highest traffic will be on top of the list:

```bash
https://test.api.amadeus.com/v1/reference-data/locations?subType=AIRPORT&keyword=M&countryCode=US&sort=analytics.travelers.score
```

In addition to that, we can select how detailed the response will be. This is done by the optional `view` parameter, which can be:

* `LIGHT` - to only show the iataCode, name, detailedName, cityName and countryName
* `FULL` - to add on top of the LIGHT information the timeZoneOffset, geoCode, detailed address and travelers.score

The default option is `FULL`:

```bash
https://test.api.amadeus.com/v1/reference-data/locations?subType=AIRPORT&keyword=M&countryCode=US&sort=analytics.travelers.score&view=FULL
```

To search an airport or city by Id, we need to obtain the Id by using the `GET ​/reference-data​/locations` endpoint. For example:

```json
{
  "meta": {
    "count": 2,
    "links": {
      "self": "https://test.api.amadeus.com/v1/reference-data/locations?subType=CITY,AIRPORT&keyword=MUC&countryCode=DE"
    }
  },
  "data": [
    {
      "type": "location",
      "subType": "CITY",
      "name": "MUNICH INTERNATIONAL",
      "detailedName": "MUNICH/DE:MUNICH INTERNATIONAL",
      "id": "CMUC",
      "self": {
        "href": "https://test.api.amadeus.com/v1/reference-data/locations/CMUC",
        "methods": [
          "GET"
        ]
      },
      "timeZoneOffset": "+02:00",
      "iataCode": "MUC",
      "geoCode": {
        "latitude": 48.35378,
        "longitude": 11.78609
      },
      "address": {
        "cityName": "MUNICH",
        "cityCode": "MUC",
        "countryName": "GERMANY",
        "countryCode": "DE",
        "regionCode": "EUROP"
      },
      "analytics": {
        "travelers": {
          "score": 27
        }
      }
    },
    {
      "type": "location",
      "subType": "AIRPORT",
      "name": "MUNICH INTERNATIONAL",
      "detailedName": "MUNICH/DE:MUNICH INTERNATIONAL",
      "id": "AMUC",
      "self": {
        "href": "https://test.api.amadeus.com/v1/reference-data/locations/AMUC",
        "methods": [
          "GET"
        ]
      },
      "timeZoneOffset": "+02:00",
      "iataCode": "MUC",
      "geoCode": {
        "latitude": 48.35378,
        "longitude": 11.78609
      },
      "address": {
        "cityName": "MUNICH",
        "cityCode": "MUC",
        "countryName": "GERMANY",
        "countryCode": "DE",
        "regionCode": "EUROP"
      },
      "analytics": {
        "travelers": {
          "score": 27
        }
      }
    }
  ]
}
```

The Id for the city of Munich is `CMUC`. However, for the Munich Airport the Id will be `AMUC`. Once we know this Id, we can use it to call the `GET ​/reference-data​/locations//reference-data/locations/{locationId}`, as it is the only parameter that the query requires:

```bash
GET https://test.api.amadeus.com/v1/reference-data/locations/CMUC
```

### Compare the flight price to historical fares

When booking a flight, travelers need to be confident that they're getting a good deal. You can compare a flight price to historical fares for the same flight route using the [Flight Price Analysis API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-price-analysis){:target="\_blank"}. It uses an Artificial Intelligence algorithm trained on Amadeus historical flight booking data to show how current flight prices compare to historical fares and whether the price of a flight is below or above average.

The only mandatory parameters for this search are the origin airport IATA code, destination airport IATA code and the departure date in the ISO 8601 YYYY-MM-DD format.

Let's see how it works. In our example we will be flying from Madrid (MAD) to Paris (CDG) on 12 December 2022:

```bash
https://test.api.amadeus.com/v1/analytics/itinerary-price-metrics?originIataCode=MAD&destinationIataCode=CDG&departureDate=2022-12-12
```

This is what we get in the response:

```json
{
  "warnings": [],
  "data": [
    {
      "type": "itinerary-price-metric",
      "origin": {
        "iataCode": "MAD"
      },
      "destination": {
        "iataCode": "CDG"
      },
      "departureDate": "2022-12-12",
      "transportType": "FLIGHT",
      "currencyCode": "EUR",
      "oneWay": true,
      "priceMetrics": [
        {
          "amount": "29.59",
          "quartileRanking": "MINIMUM"
        },
        {
          "amount": "76.17",
          "quartileRanking": "FIRST"
        },
        {
          "amount": "129.24",
          "quartileRanking": "MEDIUM"
        },
        {
          "amount": "185.59",
          "quartileRanking": "THIRD"
        },
        {
          "amount": "198.15",
          "quartileRanking": "MAXIMUM"
        }
      ]
    }
  ],
  "meta": {
    "count": 1,
    "links": {
      "self": "https://test.api.amadeus.com/v1/analytics/flight-price-metrics?originIataCode=MAD&destinationIataCode=CDG&departureDate=2022-12-12&currencyCode=EUR&oneWay=True"
    }
  }
}
```

By default the price will be shown in Euros. In this example we can see that the lowest price for such ticket should be 29.59 Euros and the highest 198.15 Euros. The first, medium and trird choices give you an idea about the possible price ranges for this flight.

We also have an option to request the result in a different currency. This is done by using the `currencyCode` parameter, which is an ISO 4217 format currency code. In addition, we can specify whether we are inquiring about a round trip or a one way ticket.

```bash
GET https://test.api.amadeus.com/v1/analytics/itinerary-price-metrics?originIataCode=MAD&destinationIataCode=CDG&departureDate=2021-03-21&currencyCode=EUR&oneWay=true
```


## Confirm Fares

The availability and price of airfare fluctuate, so it’s important to confirm
before proceeding to book. This is especially true if time passes between the
initial search and the decision to book, as fares are limited and there are
thousands of bookings occurring every minute. During this step, you can also
add ancillary products like extra bags or legroom. For that you can use the [Flight Offers Price API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-offers-price){:target="\_blank"}.

Once a flight has been selected, you’ll need to confirm the availability and
price of the fare. This is where the [Flight Offers Price API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-offers-price){:target="\_blank"} comes in. This API
returns the final fare price \(including taxes and fees\) of flights from the
[Flight Offers Search](https://developers.amadeus.com/self-service/category/air/api-doc/flight-offers-search){:target="\_blank"} as well as pricing for ancillary products and the
payment information that will be needed to make the final booking. 

The body to be sent via `POST` is built by a new object of type
`flight-offers-pricing` composed by a list of `flight-offers` (up to 6) +
payment information. In addition to this, a `X-HTTP-Method-Override` header parameter is required.

```json
{
   "data": {
        "type": "flight-offers-princing",
        "flightOffers": [
            { "type": "flight-offer" }
        ],
        "payment" : [
            { Payment_Object }
        ]
    }
```

## Return fare rules

The [Flight Offers Price API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-offers-price){:target="\_blank"} confirms the final price and availability of a fare. It also returns detailed fare rules, including the cancellation policy and other information. In addition to this, a `X-HTTP-Method-Override` header parameter is required. To get the fare rules, add the parameter `include=detailed-fare-rules` to your API call, as shown below: 

```bash
POST https://test.api.amadeus.com/v1/shopping/flight-offers/pricing?include=detailed-fare-rules
```

The `FareRules` object represents a collection of fare rules and penalties associated with a specific fare. Each rule is represented as a `TermAndCondition` object, containing information about the rule category, circumstances, applicability, maximum penalty amount, and detailed descriptions.

* `FareRules`:

    * `currency`: The currency in which the penalties are expressed.
    * `rules`: An array of `TermAndCondition` objects, each representing a specific fare rule or condition.
    
* `TermAndCondition`:
    * `category`: A string defining the type of modification concerned in the rule, such as `REFUND`, `EXCHANGE`, `REVALIDATION`, `REISSUE`, `REBOOK`, or `CANCELLATION`.
    * `circumstances`: A string providing additional information on the circumstances under which the rule applies.
    * `notApplicable`: A boolean indicating if the rule does not apply to the fare.
    * `maxPenaltyAmount`: A string representing the maximum penalty amount for the given rule.
    * `descriptions`: An array of `Description` objects that provide further details on the rule. Each `Description` object includes:
        * `descriptionType`: A string representing the type of description.
        * `text`: The actual text of the description, providing more context or explanation for the rule.

You can also see the process step to step How to display farerules in this video tutorial from [Advanced flight booking engine series](https://www.youtube.com/playlist?list=PLBehidtj-OiqHeziKjDH04IBXdvI0eBrg). 

![type:video](https://www.youtube.com/embed/CZ2bi0ifHqs)

## Check CO2 emissions data

The [Flight Offers Price API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-offers-price){:target="\_blank"} allows you to see the emissions data for your itinerary. This data is returned as part of the reponse in the following format:

```json
                "co2Emissions": [
                  {
                    "weight": 46,
                    "weightUnit": "KG",
                    "cabin": "ECONOMY"
                  }
                ]
```

* `weight` is an integer representing the weight of CO2 emitted for the concerned flight segment
* `weightUnit` is a string indicating the unit of measurement for the weight of CO2 emissions, which can be specified in either pounds or kilos.
* `cabin` is a string representing the quality of service offered in the cabin where the seat is located. This is an enum, which can be `ECONOMY`, `PREMIUM_ECONOMY`, `BUSINESS`, `FIRST`. 

## Book a Flight

Once the fare is confirmed, you’re ready to use the [Flight Create Orders API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-create-orders){:target="\_blank"}
to perform the actual booking. This API lets you log a reservation in the
airlines’ systems and create a [PNR](https://developers.amadeus.com/blog/what-is-pnr-booking-reference){:target="\_blank"}, and returns a unique Id number and the
reservation details. If you’re using an airline consolidator, the PNR will be
automatically sent to the consolidator for ticket issuance. [Visit the Flight
Create Orders documentation
page](https://developers.amadeus.com/self-service/category/air/api-doc/flight-create-orders){:target="\_blank"}
for more details on this API.

Remember, you need to be able to issue a ticket to make bookings with our
[Flight Create Orders API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-create-orders){:target="\_blank"}. To access the API in production, you need to either
sign a contract with an airline consolidator or be accredited to issue tickets
yourself.


## Issue a ticket

Once the booking is made, you need to complete payment. In most cases, you’ll
receive payment from the customer and then pay the airline, typically via an
industry-specific settlement procedure like the BSP or ARC \(more on those
later\).

In the final step, a flight ticket is issued. In industry terms, a flight
ticket is a confirmation that payment has been received, the reservation has
been logged, and the customer has the right to enjoy the flight. For [IATA
member airlines](https://www.iata.org/about/members/Pages/airline-list.aspx){:target="\_blank"},
only certain accredited parties can issue tickets. In the next section, we’ll
go into detail about your options for managing this final step in the booking
process.

You can see How to manage and issue flight booking process in this video tutorial from [Flight Booking Engine 101 series](https://www.youtube.com/playlist?list=PLBehidtj-OipMAl97bHV0pxHh9yGdOrdh). 

![type:video](https://www.youtube.com/embed/--oFZEbMcmk)

If you are interested in knowing more about issuing tickets in travel industry, please check out this [article](https://developers.amadeus.com/blog/what-is-air-ticketing){:target="\_blank"}. 

## View the aircraft cabin layout

With the [Seatmap Display API](https://developers.amadeus.com/self-service/category/air/api-doc/seatmap-display){:target="\_blank"} you can view the aircraft cabin layout: 

- `deckConfiguration` - the dimensions of the passenger deck in (x,y) coordinates, including the location of the wings, exit rows, and cabins. These dimensions form a grid on which you will later place facilities and seats.
- `facilities` - the (x,y) coordinates of aircraft facilities, such as bathrooms or galleys.
- `seats` - the (x,y) coordinates of all seats on the aircraft, with their respective availability status, characteristics, and prices.

To help you build a more consistent display, the API returns a uniform width for all cabins and classes. Rows with special seating like business class or extra-legroom seats have fewer seats per row (e.g., 4 seats for width of 7 coordinates) than economy rows (e.g. 7 seats for a width of 7 coordinates).


You can see the more details about the aircraft cabin layout in the video below. 

![type:video](https://www.youtube.com/embed/uTOQjGsZLfI)

### Display in-flight amenities

Both endpoints of the [Seatmap Display API](https://developers.amadeus.com/self-service/category/air/api-doc/seatmap-display){:target="\_blank"} return information about the following in-flight amenities:

- Seat
- Wi-fi
- Entertainment
- Power
- Food
- Beverage

### Select a seat 

Requests to either endpoint of the [Seatmap Display API](https://developers.amadeus.com/self-service/category/air/api-doc/seatmap-display){:target="\_blank"} will return a list of seating options with their characteristics, pricing, and coordinates. Let's look at an example response:

```json
{
                "cabin": "M",
                "number": "20D",
                "characteristicsCodes": [
                  "A",
                  "CH",
                  "RS"
                ],
                "travelerPricing": [
                  {
                    "travelerId": "1",
                    "seatAvailabilityStatus": "AVAILABLE",
                    "price": {
                      "currency": "EUR",
                      "total": "17.00",
                      "base": "17.00",
                      "taxes": [
                        {
                          "amount": "0.00",
                          "code": "SUPPLIER"
                        }
                      ]
                    }
                  }
                ],
                "coordinates": {
                  "x": 10,
                  "y": 4
                }
              },
```

For each seat, the [Seatmap Display API](https://developers.amadeus.com/self-service/category/air/api-doc/seatmap-display){:target="\_blank"} provides a seatAvailabilityStatus so you can indicate which seats are currently available for booking. Seats may have one of three availability statuses:

- `AVAILABLE` – the seat is not occupied and is available to book.
- `BLOCKED` – the seat is not occupied but isn’t available to book for the user. This is usually due to the passenger type (e.g., children may not sit in exit rows) or their fare class (e.g., some seats may be reserved for flyers in higher classes).
- `OCCUPIED` – the seat is  occupied and unavailable to book.

If a flight is fully booked, the API returns an OCCUPIED status for all seats. In most cases, fully booked flights are filtered out during search with the [Flight Offers Search API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-offers-search){:target="\_blank"} or when confirming the price with the [Flight Offers Price API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-offers-price){:target="\_blank"}. The [Flight Create Orders API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-create-orders){:target="\_blank"} returns an error message if you try to book an unavailable seat. For more information on the booking flow, check out how to build a flight booking engine.

Once your user has selected their seat, the next step is to add the desired seat to the flight offer and prepare them for booking.

In the above example response, seat `20D` is indicated as `AVAILABLE`. For your user to be able to book the seat, you must add the seat to the flightOffer object and call [Flight Offers Price](https://developers.amadeus.com/self-service/category/air/api-doc/flight-offers-price){:target="\_blank"} to get a final order summary with the included seat.

To include the seat in the `flightOffer` object, add it to `fareDetailsBySegment` → `additionalServices` → `chargeableSeatNumber`, as shown below:

```json
"fareDetailsBySegment": [
            {
            "additionalServices": {
             "chargeableSeatNumber": "20D"
              },
              "segmentId": "60",
              "cabin": "ECONOMY",
              "fareBasis": "NLYO5L",
              "brandedFare": "LITE",
              "class": "N",
              "includedCheckedBags": {
                "quantity": 0
              }
            }
          ]
```

The [Flight Offers Price API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-offers-price){:target="\_blank"} then returns the `flightOffer` object with the price of the chosen seat included within `additionalServices`:

```json
"additionalServices":
            {
              "type": "SEATS",
              "amount": "17.00"
            }
```

You can use the same process to select seats for multiple passengers. For each passenger, you must add the selected seats in `fareDetailsBySegment` for each `travelerId` within the flight offer.

At this point, you now have a priced `flightOffer` which includes your user's selected seat. The final step is to book the flight using the [Flight Create Orders API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-create-orders){:target="\_blank"}. To do this, simply pass the `flightOffer` object into a request to the [Flight Create Orders API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-create-orders){:target="\_blank"}, which will book the flight and return an order summary and a booking Id.

## Add additional baggage

### Search additional baggage options

The first step is to find the desired flight offer using the [Flight Offers Search API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-offers-search){:target="\_blank"}. Each flight offer contains an `additionalServices` field with the types of additional services available, in this case bags, and the maximum price of the first additional bag. Note that at this point, the price is for informational purposes only.  


To get the final price of the added baggage with the airline policy and the traveler's tier level taken into account, you must call the [Flight Offers Price API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-offers-price){:target="\_blank"}. To do this, add the `include=bags` parameter in the path of the [Flight Offers Price API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-offers-price){:target="\_blank"}: 


```bash
POST https://test.api.amadeus.com/v1/shopping/flight-offers/pricing?include=bags 
```

As you see below, the API returns the catalog of baggage options with the price and quantity (or weight): 

```json
"bags": { 
    "1": { 
        "quantity": 1, 
        "name": "CHECKED_BAG", 
        "price": { 
            "amount": "25.00", 
            "currencyCode": "EUR" 
        }, 
        "bookableByItinerary": true, 
        "segmentIds": [ 
            "1", 
            "14" 
        ], 
        "travelerIds": [ 
            "1" 
        ] 
    } 
    "2": {  
        "quantity": 2, 
        "name": "CHECKED_BAG", 
        "price": { 
            "amount": "50.00", 
            "currencyCode": "EUR" 
        }, 
        "bookableByItinerary": true, 
        "segmentIds": [ 
            "1", 
            "14" 
        ], 
        "travelerIds": [ 
            "1" 
        ] 
    } 
} 
```

The [Flight Offers Price API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-offers-price){:target="\_blank"} returns two bag offers for the given flight. The catalog shows that either one or two bags are available to be booked per passenger. Higher bag quantity will be rejected due to the airline's policy.

In the example above, the price of two bags is double that of one bag, though some airlines do offer discounts for purchasing more than one checked bag. Each bag offer is coupled to the specific segment and traveler Id returned in each bag offer. 

If there is no extra baggage service available, the API won’t return a baggage catalog. 

### Add additional baggage to the flight offer

Next, you need to add the additional baggage to the desired flight segments. This gives you the flexibility to include extra bags on only certain segments of the flight.  

Fill in `chargeableCheckedBags` with the desired quantity (or weight, depending on what the airline returns) in `travelerPricings/fareDetailsBySegment/additionalServices`, as shown below:

```json
"fareDetailsBySegment": [{ 
    "segmentId": "1", 
    "cabin": "ECONOMY", 
    "fareBasis": "TNOBAGD", 
    "brandedFare": "GOLIGHT", 
    "class": "T", 
    "includedCheckedBags": { 
        "quantity": 0 
    }, 
    "additionalServices": { 
        "chargeableCheckedBags": { 
            "quantity": 1 
        } 
    } 
}] 
```

### Confirm the final price and book


Once you’ve added the desired bags to the flight order, you need to call the [Flight Offers Price API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-offers-price){:target="\_blank"} to get the final price of the flight with all additional services included. Once this is done, you can then call the [Flight Create Orders API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-create-orders){:target="\_blank"} to book the flight. If you want to add different numbers of bags for different itineraries, you can do it following the same flow. 

If the desired flight you want to book, does not permit the additional service, the [Flight Create Orders API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-create-orders){:target="\_blank"} will reject the booking and return the following error:


```json
{ 
    "errors": [{ 
        "status": 400, 
        "code": 38034, 
        "title": "ONE OR MORE SERVICES ARE NOT AVAILABLE", 
        "detail": "Error booking additional services" 
    }] 
} 


```
You can see the process step to step in this video tutorial.

![type:video](https://www.youtube.com/embed/YtbT2Uwq2BQ)

### Video Tutorial 

You can also see the process step to step How to add additional baggages in this video tutorial from [Advanced flight booking engine series](https://www.youtube.com/playlist?list=PLBehidtj-OiqHeziKjDH04IBXdvI0eBrg). 

![type:video](https://www.youtube.com/embed/zCKxgZt5KhQ)


## Check the flight status

The [On-Demand Flight Status API](https://developers.amadeus.com/self-service/category/air/api-doc/on-demand-flight-status){:target="\_blank"} provides real-time flight schedule data including up-to-date departure and arrival times, terminal and gate information, flight duration and real-time delay status.

To get this information, the only mandatory parameters to send a query are the IATA carrier code, flight number and scheduled departure date, and you'll be up to date about your flight schedule. For example, checking the Iberia flight 532 on 23 March 2022:

```shell
https://test.api.amadeus.com/v2/schedule/flights?carrierCode=IB&flightNumber=532&scheduledDepartureDate=2022-03-23
```

If the flight changes and the carrier assigns a prefix to the flight number to indicate the change, you can specify it in the query using the additional one-letter `operationalSuffix` parameter:

```shell
https://test.api.amadeus.com/v2/schedule/flights?carrierCode=IB&flightNumber=532&scheduledDepartureDate=2021-03-23&operationalSuffix=A
```

The example response looks as follows:

```json
{
  "meta": {
    "count": 1,
    "links": {
      "self": "https://test.api.amadeus.com/v2/schedule/flights?carrierCode=AZ&flightNumber=319&scheduledDepartureDate=2021-03-13"
    }
  },
  "data": [
    {
      "type": "DatedFlight",
      "scheduledDepartureDate": "2021-03-13",
      "flightDesignator": {
        "carrierCode": "AZ",
        "flightNumber": 319
      },
      "flightPoints": [
        {
          "iataCode": "CDG",
          "departure": {
            "timings": [
              {
                "qualifier": "STD",
                "value": "2021-03-13T11:10+01:00"
              }
            ]
          }
        },
        {
          "iataCode": "FCO",
          "arrival": {
            "timings": [
              {
                "qualifier": "STA",
                "value": "2021-03-13T13:15+01:00"
              }
            ]
          }
        }
      ],
      "segments": [
        {
          "boardPointIataCode": "CDG",
          "offPointIataCode": "FCO",
          "scheduledSegmentDuration": "PT2H5M"
        }
      ],
      "legs": [
        {
          "boardPointIataCode": "CDG",
          "offPointIataCode": "FCO",
          "aircraftEquipment": {
            "aircraftType": "32S"
          },
          "scheduledLegDuration": "PT2H5M"
        }
      ]
    }
  ]
}
```



## Check for any flight delays

For any traveller it's quite important to know how far in advance they should get to the airport. The [Flight Delay Prediction API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-delay-prediction){:target="\_blank"} estimates the probability of a specific flight being delayed. 

The query consists of ten mandatory parameters:

* `originLocationCode` - IATA code of the city or airport from which the traveler is departing, e.g. `PAR` for Paris
* `destinationLocationCode` - IATA code of the city or airport to which the traveler is going, e.g. `PAR` for Paris
* `departureDate` - the date on which the traveler will depart from the origin to go to the destination in the ISO 8601 YYYY-MM-DD format, e.g. `2019-12-25`
* `departureTime` - local time relative to `originLocationCode` on which the traveler will depart from the origin in the ISO 8601 format, e.g. `13:22:00`
* `arrivalDate` - the date on which the traveler will arrive to the destination from the origin in the ISO 8601 in the YYYY-MM-DD format, e.g. `2019-12-25`
* `arrivalTime` - local time relative to `destinationLocationCode` on which the traveler will arrive to destination in the ISO 8601 standard. e.g. `13:22:00`
* `aircraftCode` - IATA [aircraft code](http://www.flugzeuginfo.net/table_accodes_iata_en.php){:target="\_blank"}
* `carrierCode` - airline / carrier code, e.g. `TK`
* `flightNumber` - flight number as assigned by the carrier, e.g. `1816`
* `duration` - flight duration in the ISO 8601 `PnYnMnDTnHnMnS` format, e.g. `PT2H10M`

```shell
GET https://test.api.amadeus.com/v1/travel/predictions/flight-delay?originLocationCode=NCE&destinationLocationCode=IST&departureDate=2020-08-01&departureTime=18%3A20%3A00&arrivalDate=2020-08-01&arrivalTime=22%3A15%3A00&aircraftCode=321&carrierCode=TK&flightNumber=1816&duration=PT31H10M
```

The response result will look as follows:


```json
{
  "data": [
    {
      "id": "TK1816NCEIST20200801",
      "probability": "0.13336977",
      "result": "LESS_THAN_30_MINUTES",
      "subType": "flight-delay",
      "type": "prediction"
    },
    {
      "id": "TK1816NCEIST20200801",
      "probability": "0.42023364",
      "result": "BETWEEN_30_AND_60_MINUTES",
      "subType": "flight-delay",
      "type": "prediction"
    },
    {
      "id": "TK1816NCEIST20200801",
      "probability": "0.34671372",
      "result": "BETWEEN_60_AND_120_MINUTES",
      "subType": "flight-delay",
      "type": "prediction"
    },
    {
      "id": "TK1816NCEIST20200801",
      "probability": "0.09968289",
      "result": "OVER_120_MINUTES_OR_CANCELLED",
      "subType": "flight-delay",
      "type": "prediction"
    }
  ],
  "meta": {
    "count": 4,
    "links": {
      "self": "https://test.api.amadeus.com/v1/travel/predictions/flight-delay?originLocationCode=NCE&destinationLocationCode=IST&departureDate=2020-08-01&departureTime=18:20:00&arrivalDate=2020-08-01&arrivalTime=22:15:00&aircraftCode=321&carrierCode=TK&flightNumber=1816&duration=PT31H10M"
    }
  }
}
```

The main parameter of the dataset is the `result`, which contains a self-explanatory value, e.g. `LESS_THAN_30_MINUTES`, `BETWEEN_30_AND_60_MINUTES`, etc.


## Check the on-time performance of an airport

Another way to get prepared for any delays, is checking the on-time performance of the actual airport. The [Airport On-Time Performance API](https://developers.amadeus.com/self-service/category/air/api-doc/airport-on-time-performance){:target="\_blank"} estimates the probability of a specific flight being delayed. 

The search query is very simple. In our query we only need to provide our flight departure date and the departure airport. For example, JFK on 12 December 2022.


```bash
GET https://test.api.amadeus.com/v1/airport/predictions/on-time?airportCode=JFK&date=2022-12-12 
```

This is the result:

```json
{
  "data": {
    "id": "JFK20221212",
    "probability": "0.928",
    "result": "0.77541769",
    "subType": "on-time",
    "type": "prediction"
  },
  "meta": {
    "links": {
      "self": "https://test.api.amadeus.com/v1/airport/predictions/on-time?airportCode=JFK&date=2022-12-12"
    }
  }
}
```

The `probability` parameter shows the probability of the airport running smoothly. In our example, this metric means that there is a 92.8% chance that there will be no delays.

## Get a direct link to the airline check-in page

Suppose we are building an app with an integrated check-in flow for a particular airline. In this case, we can leverage the [Flight Check-in Links  API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-check-in-links){:target="\_blank"} to generate a link to the airline's official check-in page in a required language for both web and mobile platforms. The only parameter that we need to provide in our search query is the airline's IATA code. If required, we can request the links in a specific language, such as UK English (en-GB). This is what our request would look like:


```bash
curl --request GET \
     --header 'Authorization: Bearer <token>' \
     --url https://test.api.amadeus.com/v2/reference-data/urls/checkin-links?airlineCode=BA&language=en-GB \
```

This is what we get in the response:

```json
{
  "meta": {
    "count": 3,
    "links": {
      "self": "https://test.api.amadeus.com/v2/reference-data/urls/checkin-links?airlineCode=BA&language=EN-GB"
    }
  },
  "data": [
    {
      "type": "checkin-link",
      "id": "BAEN-GBAll",
      "href": "https://www.britishairways.com/travel/olcilandingpageauthreq/public/en_gb",
      "channel": "All"
    },
    {
      "type": "checkin-link",
      "id": "BAEN-GBMobile",
      "href": "https://www.britishairways.com/travel/olcilandingpageauthreq/public/en_gb/device-mobile",
      "channel": "Mobile"
    },
    {
      "type": "checkin-link",
      "id": "BAEN-GBWeb",
      "href": "https://www.britishairways.com/travel/olcilandingpageauthreq/public/en_gb",
      "channel": "Web"
    }
  ]
}
```

Here we've got a dedicated link for web applications, a dedicated link for mobile applications and a link that works on all platforms.


## Cancel a reservation

Just as you can help users book a flight with the [Flight Create Orders API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-create-orders){:target="\_blank"}, you can now also help them cancel their reservations with the [Flight Order Management](https://developers.amadeus.com/self-service/category/air/api-doc/flight-order-management){:target="\_blank"} API. However, you have a limited window of time to cancel via API. If you’re working with an airline consolidator for ticketing, cancellations via API are generally only allowed while the order is queued for ticketing. Once the ticket has been issued, you’ll have to contact your consolidator directly to handle the cancellation.

To call the [Flight Order Management API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-order-management){:target="\_blank"}, you have pass as a parameter the flight-orderId from the [Flight Create Orders API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-create-orders){:target="\_blank"}.

To retrieve the flight order data:

```bash
GET https://test.api.amadeus.com/v1/booking/flight-orders/eJzTd9f3NjIJdzUGAAp%2fAiY
```

To delete the flight order data:


```bash
DELETE https://test.api.amadeus.com/v1/booking/flight-orders/eJzTd9f3NjIJdzUGAAp%2fAiY
```

## View reservation details

With the [Flight Order Management API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-order-management){:target="\_blank"} you can consult and check your flight reservation. 

To call the [Flight Order Management API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-order-management){:target="\_blank"}, you have pass as a parameter the flight-orderId from the [Flight Create Orders API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-create-orders){:target="\_blank"}, such as:

```bash
GET https://test.api.amadeus.com/v1/booking/flight-orders/eJzTd9f3NjIJdzUGAAp%2fAiY
```

## Common Errors

### Issuance not allowed in Self Service

Self-Service users must work with an airline consolidator that can issue
tickets on your behalf. In that case, the payment is not processed by the API
but directly between you and the consolidator. Adding a form of payment to
the [Flight Create Orders API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-create-orders){:target="\_blank"} will be rejected by error INVALID FORMAT.

### Price discrepancy 

The price of airfare fluctuates constantly. Creating an order for a flight whose price is no longer valid at the time of booking will trigger the
following error:

```json
{
  "errors": [
    {
      "status": 400,
      "code": 37200,
      "title": "PRICE DISCREPANCY",
      "detail": "Current grandTotal price (2780.28) is different from request one (2779.58)"
    }
  ]
}
```

If you receive this error, reconfirm the fare price with the [Flight Offers Price API](https://developers.amadeus.com/self-service/category/air/api-doc/flight-offers-price){:target="\_blank"} before booking.


The following is a common error in the test environment, as you can perform many bookings without restrictions (no real payment), but the inventory is a copy of the real one, so if you book many seats, the inventory will be empty and you won't be able to book anymore.

```json
{
            "status": 400,
            "code": 34651,
            "title": "SEGMENT SELL FAILURE",
            "detail": "Could not sell segment 1"
        }
```

## Notes

### Carriers and rates

- Low cost carriers (LCCs), American Airlines are not available. Depending on the market, British Airways is also not available.
- Published rates only returned in Self-Service. Cannot access to negotiated rates, or any other special rates. 

### Post-booking modifications 

With the current version of our Self-Service APIs, you can’t add additional baggage after the flight has been booked. This and other post-booking modifications must be handled directly with the airline consolidator that is issuing tickets on your behalf.   

### How payment works

There are two things to consider regarding payments for flight booking:

- The payment between you (the app owner) and your customers (for the services provided + the price of the flight ticket). You decide how to collect this payment, it is not included in the API. A third party payment gateway, such as Stripe will be an easier solution for this.
- The payment between you and the consolidator (to be able to pay the airline and issue the flight ticket). This will be done between you and your consolidator of choice, and is to be agreed with the consolidator.


### Flight Booking Engine 101 Video tutorial 

A [video tutorial series](https://youtube.com/playlist?list=PLBehidtj-OipMAl97bHV0pxHh9yGdOrdh){:target="\_blank"} to Explain Flight Booking Engine is available in Youtube channel. 

![type:video](https://www.youtube.com/embed/2Jh3ouEe2ws)
