# Holiday API for JavaScript/TypeScript
<!-- TODO badges -->
Industry-leading Holiday API for JavaScript/TypeScript. Over 5,000 holidays and thousands of descriptions. Trusted by the World’s leading companies. Built by developers for developers since 2011.

# Authentication
Access to the Holiday API requires an API Key. You can get for one for FREE [here](https://apilayer.com/marketplace/checkiday-api#pricing), no credit card required! Note that free plans are limited. To access more data and have more requests, a paid plan is required.

# Example Usage

## Authentication
Simply construct an instance of `HolidayApi` and pass your API Key like this:
```ts
const api = new HolidayApi({ apiKey: '<Your API Key Here>' });
```

## Get Events
Get all events for a specified date.

```ts
const response = await api.getEvents({
  // Include events that may be unsafe for viewing at work or by children. Default is false.
  adult: true,
  // IANA Time Zone for calculating dates and times. Defaults to America/Chicago.
  timezone: 'America/New_York',
  // Date to get the events for. Defaults to today.
  date: '5/5/2025',
});
```

Example response:
```json
{
    "timezone": "America/New_York",
    "date": "05/05/2025",
    "adult": true,
    "events": [
        {
            "id": "b80630ae75c35f34c0526173dd999cfc",
            "name": "Cinco de Mayo",
            "url": "https://www.checkiday.com/b80630ae75c35f34c0526173dd999cfc/cinco-de-mayo"
        },
        // and more ...
        {
            "id": "346052f12d9209ef2119f45565a47279",
            "name": "Totally Chipotle Day",
            "url": "https://www.checkiday.com/346052f12d9209ef2119f45565a47279/totally-chipotle-day"
        }
    ],
    "multiday_starting": [
        {
            "id": "b9321bf3ce70e98fb385cb03d2f0cac4",
            "name": "Teacher Appreciation Week",
            "url": "https://www.checkiday.com/b9321bf3ce70e98fb385cb03d2f0cac4/teacher-appreciation-week"
        }
    ],
    "multiday_ongoing": [
        {
            "id": "676cd91e31adcacd0a505117d2c4a842",
            "name": "Be Kind to Animals Week",
            "url": "https://www.checkiday.com/676cd91e31adcacd0a505117d2c4a842/be-kind-to-animals-week"
        },
        // and more ...
        {
            "id": "9cc82cc56178ba41f120381a4d6e5213",
            "name": "Syringomyelia Awareness Month",
            "url": "https://www.checkiday.com/9cc82cc56178ba41f120381a4d6e5213/syringomyelia-awareness-month"
        }
    ]
}
```

## Search For Events
Search for events with a specified query.

```ts
const response = await api.search({
  // The search query. Must be at least 3 characters long.
  query: 'zucchini',
  // Include events that may be unsafe for viewing at work or by children. Default is false.
  adult: true,
});
```

Example response:
```json
{
    "query": "zucchini",
    "adult": true,
    "events": [
        {
            "id": "cc81cbd8730098456f85f69798cbc867",
            "name": "National Zucchini Bread Day",
            "url": "https://www.checkiday.com/cc81cbd8730098456f85f69798cbc867/national-zucchini-bread-day"
        },
        {
            "id": "778e08321fc0ca4ec38fbf507c0e6c26",
            "name": "National Zucchini Day",
            "url": "https://www.checkiday.com/778e08321fc0ca4ec38fbf507c0e6c26/national-zucchini-day"
        },
        {
            "id": "61363236f06e4eb8e4e14e5925c2503d",
            "name": "Sneak Some Zucchini Onto Your Neighbor's Porch Day",
            "url": "https://www.checkiday.com/61363236f06e4eb8e4e14e5925c2503d/sneak-some-zucchini-onto-your-neighbors-porch-day"
        }
    ]
}
```

## Get Event Information
Get additional information for an Event.

```ts
const response = await api.getEventInfo({
  // The ID of the requested Event.
  id: 'f90b893ea04939d7456f30c54f68d7b4',
  // The starting range of returned occurrences. Optional, defaults to 2 years prior.
  start: 2001,
  // The ending range of returned occurrences. Optional, defaults to 3 years in the future.
  end: 2003,
});
```

Example response:
```json
{
    "event": {
        "id": "f90b893ea04939d7456f30c54f68d7b4",
        "name": "International Cat Day",
        "alternate_names": [],
        "adult": false,
        "url": "https://www.checkiday.com/f90b893ea04939d7456f30c54f68d7b4/international-cat-day",
        "hashtags": [
            "InternationalCatDay",
            "CatDay"
        ],
        "image": {
            "small": "https://static.checkiday.com/img/300/kittens-555822.jpg",
            "medium": "https://static.checkiday.com/img/600/kittens-555822.jpg",
            "large": "https://static.checkiday.com/img/1200/kittens-555822.jpg"
        },
        "sources": [
            "https://www.ibtimes.com/international-cat-day-2014-cat-lovers-worldwide-celebrate-feline-obsession-1653614",
            "https://www.ifaw.org/united-states/news/ifaw-marks-international-cat-day"
        ],
        "founders": [
            {
                "name": "International Fund For Animal Welfare",
                "url": "https://www.ifaw.org/",
                "date": "2002"
            }
        ],
        "description": {
            "text": "International Cat Day celebrates love for cats...",
            "html": "<p>International Cat Day celebrates love for cats...",
            "markdown": "International Cat Day celebrates love for cats..."
        },
        "how_to_observe": {
            "text": "Spend the day playing with your cat...",
            "html": "<p>Spend the day playing with your cat...",
            "markdown": "Spend the day playing with your cat..."
        },
        "patterns": [
            {
                "first_year": 2002,
                "last_year": null,
                "observed": "annually on August 8th",
                "observed_html": "annually on <a href=\"https://www.checkiday.com/8/8\">August 8th</a>",
                "observed_markdown": "annually on [August 8th](https://www.checkiday.com/8/8)",
                "length": 1
            }
        ],
        "occurrences": [
            {
                "date": "08/08/2002",
                "length": 1
            },
            {
                "date": "08/08/2003",
                "length": 1
            }
        ]
    }
}
```

<!-- TODO errors -->