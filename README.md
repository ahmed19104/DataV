# BankLytics - Bank Customer Feedback Dashboard

A static, multi-page **data visualization dashboard** that analyzes customer feedback about five US banks. It loads a cleaned CSV in the browser and renders interactive charts, with no backend.

## Pages

| Page | File | What it shows |
| --- | --- | --- |
| Executive Summary | `index.html` | KPIs (volume, sentiment, resolved share, priority), sentiment breakdown, resolution performance, volume by source, bank comparison |
| Sentiment & Topics | `topics.html` | Feedback trend over time, topics by resolution status, sentiment distribution, pain-points heatmap |
| Operations & Support | `operations.html` | Resolution by priority, SLA performance vs target, live feedback stream |
| Influence Radar | `influence.html` | Topic impact vs reach (bubble), top geographies, topic sentiment footprint, follower count vs sentiment |

Every page has a bank selector (**All Banks Portfolio** or a single bank).

## Dataset

`D1_Cleaned.csv` has **500 feedback records** (100 per bank) from **2025-11-17 to 2026-02-22**.

| Column | Description |
| --- | --- |
| `Id` | Feedback id (for example `FBK-1001`) |
| `BankName` | Chase Bank, Bank of America, Citibank, Capital One, PNC |
| `CreatedAt` | Timestamp |
| `Source` | Twitter, App Store, Google Play, Support Email, Search |
| `SentimentScore` | Numeric score |
| `SentimentCategory` | Positive, Neutral, Negative |
| `Topic` | Fraud Alert, Credit Card, Hidden Fees, Customer Service, Mobile App, Loan Application, Website Bug |
| `FeedbackText` | The customer comment |
| `AuthorUsername`, `FollowersCount`, `Location` | Author and reach details |
| `IsResolved` | Whether the issue was resolved |
| `Priority` | High, Medium, Low |

## Tech stack

- HTML5 and [Tailwind CSS](https://tailwindcss.com) (CDN)
- [Chart.js](https://www.chartjs.org) for charts
- [PapaParse](https://www.papaparse.com) for CSV parsing
- Vanilla JavaScript

## Project structure

```
DataV/
├── index.html        # Executive Summary
├── topics.html       # Sentiment & Topics
├── operations.html   # Operations & Support
├── influence.html    # Influence Radar
└── D1_Cleaned.csv    # Dataset
```

## Run it

The pages fetch the CSV, so serve the folder over HTTP instead of opening the files directly:

```bash
git clone https://github.com/ahmed19104/DataV.git
cd DataV
python -m http.server 8000
# open http://localhost:8000
```

Or publish it with GitHub Pages. An internet connection is needed for the CDN libraries.

## Author

**Ahmed Yaser** - [@ahmed19104](https://github.com/ahmed19104)
