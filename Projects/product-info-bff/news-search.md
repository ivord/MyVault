---
type: note
title: "NewsSearch — market_news_for_you handler"
tags: [go, bff, cafe-api, news, handler]
file: pkg/handlers/market_news_for_you.go
created: 2026-05-31
---

# NewsSearch

## Location
`pkg/handlers/market_news_for_you.go:242`

## Function
```go
func mapArticlesV1WithV2Client(c *fiber.Ctx, cafeClient *client.Client, request dto.NewsSearchRequest) ([]dto.Article, any, error) {
    resp, httpStatusCode, err := cafeClient.NewsSearch(c, request)
    if err != nil || httpStatusCode != 200 {
        logger.LogError("cannot get news search response")
        return nil, nil, fmt.Errorf("cannot get news search response")
    }
    articles := mapNewsContents(resp.Data.Contents)

    hasNextPage := resp.Data.Pagination.HasNextPage != nil && *resp.Data.Pagination.HasNextPage
    if hasNextPage && len(articles) < request.Limit {
        hasNextPage = false
    }

    totalPages := request.Page
    if hasNextPage {
        totalPages = request.Page + 1
    }
    pagination := dto.Pagination{
        PaginationV2: dto.PaginationV2{HasNextPage: &hasNextPage},
        Limit:        request.Limit,
        Page:         request.Page,
        TotalPages:   totalPages,
    }
    return articles, pagination, nil
}
```

## Notes
- Calls `cafeClient.NewsSearch` (Café API v2 client)
- Maps raw contents → `[]dto.Article` via `mapNewsContents`
- Adjusts `hasNextPage` if returned articles < requested limit (edge case guard)
- Returns pagination struct with `HasNextPage`, `Limit`, `Page`, `TotalPages`
- Part of portfolio-aware personalized news flow (News-For-You handler)
