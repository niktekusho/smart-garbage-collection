# Data analysis

In this document I go through some or all the data structures that will be used in the project (depending on the spare time I have 😄).

# City

Cities should be referred to them by name and country (in case of namesakes), name and city id (zip code), geographic coordinates.

Cities should be able to present or link to their public institutional website; I think also a quick way to send feedbacks should be present therefore there should be contact info like addresses, phone numbers and maybe opening hours and days.

A list of "subcities" should be present as those may have other collection policies. Here in Italy we have the [__comune__](https://en.wikipedia.org/wiki/Comune) and several smaller [__frazioni__](https://en.wikipedia.org/wiki/Frazione) inside of it and in several (if not all) of them the collection days are different.

## Example of a City model

| Data _Name_       | Type          | Details                                        |
| ----------------- | ------------- | ---------------------------------------------- |
| City Name         | `String`      | Name of the city                               |
| Submunicipalities | `City[]`      | List of smaller "cities" inside the city.      |
| City ID           | `String`      | ID (Zip code/_CAP_ in Italy e.g.) of the city. |
| Country           | `Enum/String` | Name of the country.                           |
| Contact Info      | `ContactInfo` | Links to public offices addresses and as such. |
| Coordinates       | `Location`    | Geographic coordinates.                        |

# Collection info

Every garbage collection should have the usual days of the week, the frequency of the collection and maybe even the time of the day of the collection.

Since separate collection exists in many countries, it should be supported OOTB. Separate collection involves determining what kind of waste is collected in each collection (metal, glass, plastic, organic, not recyclable, etc.).

## Example of a Collection info model

| Data _Name_      | Type             | Details                                                                                                       |
| ---------------- | ---------------- | ------------------------------------------------------------------------------------------------------------- |
| Day of the week  | `Integer/String` | Day of the week: could be integer starting from monday or sunday (depending on locale) or just plain strings. |
| Frequency        | `Frequency`      | Dedicated object that defines occurence repetitions.                                                          |
| Waste Collection | `Enum/String`    | Option from a predefined list or just normal strings.                                                         |

# Other

Since garbage collection is something that often is repeated regularly (exceptions can be found only during festivities and in critical environments (like staff strikes, any kind of disasters, etc.)), there should be a "generator" that takes the calendar and for each collection places a collection event on it based on day of the week and frequency.
