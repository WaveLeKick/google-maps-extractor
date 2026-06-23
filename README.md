[Google Maps Extractor](https://apify.com/cloway/google-maps-extractor?fpr=data)

Extract business data from Google Maps search results for any Brazilian city. Get structured data including business name, rating, reviews, address, phone, website, category, and coordinates.

## What it does

This actor searches Google Maps for businesses in Brazilian cities and extracts structured data from the results. Simply provide a search query like "restaurantes em Sao Paulo" or "dentistas Curitiba" and get back a clean JSON dataset.

### Data extracted for each business

| Field | Description |
| --- | --- |
| name | Business name |
| rating | Average rating (1-5 stars) |
| reviewCount | Total number of reviews |
| address | Full street address |
| phone | Phone number |
| website | Website URL |
| category | Business category (e.g., "Restaurante italiano") |
| latitude | GPS latitude |
| longitude | GPS longitude |
| googleMapsUrl | Direct link to Google Maps |

## Use cases

- **Lead generation**: Build targeted lists of businesses by city and category for sales outreach
- **Market research**: Analyze business density, ratings, and competition across Brazilian cities
- **Competitor analysis**: Monitor competitors' ratings, review counts, and presence
- **Directory building**: Create business directories for specific niches and locations
- **Local SEO analysis**: Audit local search results for SEO strategy

## Input

| Field | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| query | string | Yes | - | Search query (e.g., "restaurantes em Sao Paulo") |
| maxResults | integer | No | 10 | Maximum results to extract (1-20) |
| language | string | No | pt-BR | Language for results |
| country | string | No | BR | Country code |

### Example input

```
{
    "query": "restaurantes em Sao Paulo",
    "maxResults": 15,
    "language": "pt-BR",
    "country": "BR"
}
```

## Output

The actor outputs a dataset with one entry per business found:

```
{
    "name": "Restaurante Fasano",
    "rating": 4.6,
    "reviewCount": 2847,
    "address": "R. Vittorio Fasano, 88 - Jardim Paulista, Sao Paulo - SP",
    "phone": "(11) 3896-4000",
    "website": "https://www.fasano.com.br",
    "category": "Restaurante italiano",
    "latitude": -23.5629,
    "longitude": -46.6714,
    "googleMapsUrl": "https://www.google.com/maps/search/Restaurante+Fasano",
    "query": "restaurantes em Sao Paulo",
    "scrapedAt": "2024-01-15T10:30:00.000Z"
}
```

## Sample queries

- `restaurantes em Sao Paulo`
- `dentistas Curitiba`
- `hoteis Rio de Janeiro`
- `advogados Brasilia`
- `academias Belo Horizonte`
- `pet shops Florianopolis`

## Limitations

- Maximum 20 results per search (first page of Google Maps results)
- Google may occasionally block requests; the actor handles this gracefully
- For best results on the Apify platform, enable proxy in your Actor run configuration
- Results depend on Google's current page structure; the actor uses multiple extraction strategies as fallback

## Pricing

This actor is free to use. You only pay for the Apify platform compute units consumed during the run.

---

Built by [NomePronto](https://nomepronto.com.br) - Your business naming and registration partner in Brazil.