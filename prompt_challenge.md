# Social Media Watcher

## Goal

Write a prompt that ingests multiple social media posts (X/Twitter, Instagram, Facebook, Threads, Reddit), filters by watch tags, and emits a strict JSON report of user feedbacks. 

[POST A]
Platform: X
Handle: @flyer_j
Time: 2025-02-14 08:12 local
Text: #payment keeps failing when saving card in app. Anyone else? #bug

[POST B]
Platform: Instagram
Account: travel.finder
Time: 2025-02-14 08:35 local
Text: Search results super slow today #performance #search

[POST C]
Platform: Facebook
Page: App Fans Group
Time: 2025-02-14 08:41 local
Text: Login loop after update. Can't get past the spinner. #login #crash

[POST D]
Platform: Threads
Account: @weekendhopper
Time: 2025-02-14 09:05 local
Text: Booking went through but payment step froze once. #booking

[POST E]
Platform: Reddit
Subreddit: r/travelapps
Time: 2025-02-14 09:27 local
Text: UX on date picker is confusing. Any plan to change it? (no tags)

# Expected output
```json
{
  "feedbacks": [
    {
      "effective_day": "2025-02-14",
      "line": "Payments",
      "posts": [
        {
          "source": "X",
          "post_content": "#payment keeps failing when saving card in app. Anyone else? #bug",
          "time_of_report": "2025-02-14T08:12:00Z",
          "tags_matched": ["#payment", "#bug"],
          "url": null
        }
      ],
      "summary": "Reports of payment failures when saving card.",
      "priority": "high"
    },
    {
      "effective_day": "2025-02-14",
      "line": "Search",
      "posts": [
        {
          "source": "Instagram",
          "post_content": "Search results super slow today #performance #search",
          "time_of_report": "2025-02-14T08:35:00Z",
          "tags_matched": ["#performance", "#search"],
          "url": null,
          "priority": "high"
        }
      ],
      "summary": "Slow search results reported."
    },
    {
      "effective_day": "2025-02-14",
      "line": "Login",
      "posts": [
        {
          "source": "Facebook",
          "post_content": "Login loop after update. Can't get past the spinner. #login #crash",
          "time_of_report": "2025-02-14T08:41:00Z",
          "tags_matched": ["#login", "#crash"],
          "url": null,
          "priority": "high"
        }
      ],
      "summary": "Login loop/crash after update."
    },
    {
      "effective_day": "2025-02-14",
      "line": "Booking",
      "posts": [
        {
          "source": "Threads",
          "post_content": "Booking went through but payment step froze once. #booking",
          "time_of_report": "2025-02-14T09:05:00Z",
          "tags_matched": ["#booking"],
          "url": null,
          "priority": "low"
        }
      ],
      "summary": "Single report of freeze during booking flow."
    }
  ]
}
```

