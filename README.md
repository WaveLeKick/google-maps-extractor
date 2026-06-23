[Google Maps Extractor](https://apify.com/ghost_banana/google-maps-extractor?fpr=data)

Extract business data from Google Maps at scale. Search by keyword + location, get structured data for every result.

## What does it do?

This actor searches Google Maps for businesses matching your query and extracts:

- **Business name** and category
- **Full address** and coordinates (lat/lng)
- **Phone number** and website
- **Rating** and review count
- **Opening hours**
- **Price level** (when available)
- **Top reviews** (optional)

## Input

| Field | Type | Description | Default |
| --- | --- | --- | --- |
| `searchQueries` | Array | Search queries like "restaurants in Austin TX" | Required |
| `maxResults` | Integer | Max results per query (1-500) | 100 |
| `language` | String | Language code (en, es, fr, etc.) | en |
| `includeReviews` | Boolean | Extract top 5 reviews per business | false |

### Example Input

```
{
    "searchQueries": [
        "plumbers in Miami FL",
        "coffee shops in Portland OR"
    ],
    "maxResults": 50,
    "language": "en",
    "includeReviews": true
}
```

## Output

Each result is a JSON object:

```
{
    "name": "Joe's Plumbing",
    "category": "Plumber",
    "address": "123 Main St, Miami, FL 33101",
    "phone": "(305) 555-1234",
    "website": "joesplumbing.com",
    "rating": 4.8,
    "reviewCount": 342,
    "openingHours": "Open 24 hours",
    "priceLevel": "$$",
    "latitude": 25.7617,
    "longitude": -80.1918,
    "searchQuery": "plumbers in Miami FL",
    "topReviews": [
        {
            "author": "John D.",
            "stars": 5,
            "text": "Great service, fast response time!",
            "date": "2 weeks ago"
        }
    ]
}
```

## Use Cases

- **Lead generation**: Find businesses by industry and location
- **Market research**: Analyze competitor ratings, reviews, pricing
- **Data enrichment**: Add phone/website/coordinates to existing business lists
- **Local SEO**: Monitor business rankings and reviews across locations

## Pricing

Pay per result. Approximately $1-3 per 100 businesses extracted (depends on Apify compute usage).

## Notes

- Results depend on Google Maps availability for the search area
- Very broad queries may return fewer results than expected
- Enable "Include Reviews" for richer data (adds ~2s per business)