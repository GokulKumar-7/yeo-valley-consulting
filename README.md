# Yeo Valley Website Analytics — Consulting Project
A comprehensive web analytics consulting project analysing user behaviour, content performance, and conversion bottlenecks on Yeo Valley's newly launched website (August 2024) — using Google Analytics 4 data, Python, and structured engagement metrics to deliver actionable recommendations for improving the Yeokens loyalty programme using Python.

## Problem Statement
Yeo Valley is one of the UK's largest organic dairy companies (48th largest grocery brand, 3rd largest yogurt brand) and operates a loyalty scheme — Yeokens — with 845,878 registered accounts. Despite the launch of a new website in August 2024, only **15% of account holders** actively visit the site to bank Yeokens, and just **4.37% of total users** redeem them. This project analyses GA4 web behaviour data across acquisition channels, landing pages, content types, and user events to identify where the customer journey breaks down — and what changes would drive greater engagement, loyalty programme participation, and long-term customer retention.

## Dataset
- **Source:** Google Analytics 4 (GA4) — Yeo Valley website, provided directly by the client
- **Scope:** August 2024 – February 2025, covering all sessions, events, and content interactions
- **Fields collected:** Channel group, page path, session count, active users, engagement rate, bounce rate, scroll depth, exit count, views per session, average engagement time, event type, event count
- **Format:** Exported from GA4 as structured CSV files for downstream Python analysis

## Key Analyses

### 1. Channel-Level Performance — New vs. Returning Users
- Analysed the top 5 acquisition channels: Direct, Organic Search, Email, Referral, and Organic Social
- Segmented each channel by new vs. returning users to understand acquisition vs. retention patterns
- Identified the top 5 most visited pages per channel to uncover content performance and user intent

| Channel | New Users | Returning Users | Top Pages | User Focus |
|---------|-----------|-----------------|-----------|------------|
| Direct | 213,691 | 696,000 | `/yeokens/welcome`, `/get-banking` | Entry & Transactional |
| Organic Search | 114,367 | 317,871 | `/sign-in`, `/get-banking` | High-Intent |
| Email | 109,291 | 221,790 | `/dairy-go-round`, `/raffle` | Gamified/Rewards |
| Referral | 11,934 | 15,775 | `/dairy-go-round` | Rewards (external) |
| Organic Social | 19,472 | 3,505 | `/recipes/*` | Content Discovery |

- **Direct traffic** is the dominant retention channel — 696,000 returning users signals strong brand loyalty
- **Organic Social** shows strong new user acquisition but very low retention, suggesting content-led users do not convert to loyal site visitors

### 2. User Event Analysis — Conversion Funnel
- Mapped the full event distribution across all GA4-tracked interactions to identify friction points
- Assessed where passive visitors are failing to convert to active, engaged users

| Event | Count | Share |
|-------|-------|-------|
| `page_view` | 10,356,895 | 60.7% |
| `session_start` | 2,999,687 | 17.6% |
| `user_engagement` | 956,894 | 5.6% |
| `scroll` | 736,615 | 4.3% |
| `GA4 Yeokens Signup` | 434,583 | 2.5% |
| `form_start` | 762,275 | 4.5% |
| `form_submit` | 2,522 | 0.0% |
| `click` | 109,094 | 0.6% |
| `file_download` | 17,760 | 0.1% |

- Form starts (4.5%) with near-zero completions (0.01%) indicates severe friction in transactional flows
- 17.6% re-visit rate with low downstream conversion suggests persistent UX issues are not being resolved across sessions

### 3. Landing Page Bounce Rate vs. Engagement Rate Analysis
- Compared bounce and engagement rates for the top 10 landing pages to identify underperformers and flag outliers

| Page | Engagement Rate | Bounce Rate |
|------|-----------------|-------------|
| `/` (Homepage) | 75.4% | 24.6% |
| `/yeokens/sign-in` | 75.1% | 24.9% |
| `/yeokens/get-banking` | 48.2% | 51.8% |
| `/yeokens/welcome` | 70.3% | 29.7% |
| `/yeokens/hub` | 61.0% | 39.0% |
| `/yeokens` | 76.5% | 23.5% |
| `/yeokens/play` | 71.7% | 28.3% |
| `/yeokens/type-a-code` | 36.8% | 63.2% |

- Homepage and sign-in page perform well — strong intent-driven engagement above 75%
- `/yeokens/type-a-code` is the weakest landing page with a 63.2% bounce rate, suggesting users complete the action and exit immediately with no onward journey

### 4. Landing Page Drop-Off Analysis (Jan–Feb 2025)
- Focused on the top 10 highest-entrance pages to identify where high traffic does not translate into engagement depth
- Tracked entrances, sessions, bounce rate, engagement rate, and average engagement time

| Page | Entrances | Bounce Rate | Engagement Rate | Avg. Engagement Time |
|------|-----------|-------------|-----------------|----------------------|
| `/yeokens/dairy-go-round` | 182,316 | 37.3% | 62.7% | 9.58s |
| `/yeokens/type-a-code` | 10,691 | 11.5% | 88.4% | 12.80s |
| `/recipes/eat-your-heart-out-coconut-and-chia-j...` | 4,669 | 20.2% | 79.7% | 0.92s |
| `/our-food` | 3,942 | 14.4% | 85.5% | 25.52s |

- **Dairy-Go-Round** attracts the most visitors but has a high drop-off rate — users do not navigate beyond the game
- **Recipe pages** have near-zero average engagement time (0.92s), suggesting bounce before content loads or a poor UX first impression
- Pages for spending, banking, and raffle consistently outperform on engagement time (32.7s, 11.4s, 26.1s respectively)

### 5. High-Traffic Pages with Strong User Interaction
- Examined the top 10 pages by session volume alongside engaged sessions per active user to distinguish passive traffic from meaningful interaction

| Page | Sessions | Engaged Sessions per Active User |
|------|----------|----------------------------------|
| `/yeokens/dairy-go-round` | 302,669 | 2.92 |
| `/yeokens/get-banking` | 179,266 | 2.07 |
| `/yeokens/hub` | 132,012 | 1.79 |
| `/yeokens/play` | 69,081 | 2.70 |
| `/yeokens/raffle` | 61,503 | 1.46 |
| `/yeokens/welcome` | 23,948 | 1.08 |

- Pages with gamified or transactional functionality (Dairy-Go-Round, play, banking) drive the highest repeat engagement
- `/yeokens/welcome` shows the lowest engaged sessions per active user (1.08), suggesting onboarding flow fails to guide new users into further site activity

### 6. Blog Performance Monthly Analysis (Sep 2024 – Feb 2025)
- Evaluated blogs across 5 key metrics: total views, active users, engagement time, views per active user, and engagement time per active user
- Analysed 5 blog categories: In the Valley, Tips & Tricks, Little Ones, Nature, and Health

| Category | Active Users | Avg. Engagement Time |
|----------|-------------|----------------------|
| In the Valley | 14,488 | 32.9s |
| Health | 2,747 | 24.9s |
| Nature | 2,231 | — |
| Tips & Tricks | 930 | 36.8s |
| Little Ones | 5 | 35.4s |

- **In the Valley** drives the most traffic but lowest engagement time — users browse without reading deeply
- **Tips & Tricks** and **Little Ones** show disproportionately high engagement per user, indicating high-value niche audiences
- Overall trend: views per active user are increasing while engagement time per user is declining — users are browsing more but reading less across all blog content

### 7. Recipe Performance Monthly Analysis (Sep 2024 – Feb 2025)
- Evaluated recipe content using the same 5-metric framework as blogs
- Analysed 4 recipe categories: Desserts & Baking, Quick & Easy, Family Meals, and On the Side

| Category | Active Users | Avg. Engagement Time |
|----------|-------------|----------------------|
| Desserts & Baking | 15,319 | 31.0s |
| Family Meals | 3,746 | 26.5s |
| On the Side | 1,550 | 40.9s |
| Quick & Easy | 7,188 | 27.9s |

- **Desserts & Baking** leads in volume (15,319 users), primarily via Organic Social — visually engaging content performs well on social channels
- **On the Side** (1,550 users) records the highest engagement time (40.9s) — a strong niche audience with high intent
- Top-performing individual recipes include: courgette chocolate chip cookies, gingerbread granola, naan flatbread, kefir-marinated chicken curry, and lemon & blueberry chili cheesecake

### 8. Blogs vs. Recipes Comparison

| Metric | Blogs | Recipes |
|--------|-------|---------|
| Total Views | 75,969 | 169,880 |
| Total Active Users | 52,105 | 87,386 |
| Total Engagement Time | 1,399,925s | 2,512,368s |
| Avg. Engagement Time / User | 26.87s | 28.75s |
| Views per Active User | 1.46 | 1.94 |

- Recipes outperform Blogs across all five metrics
- Blogs show a noticeable decline in total active users over time; Recipes show slight but consistent long-term growth
- Both content types show the same browsing shift: views per active user increasing, engagement time per active user decreasing

### 9. Exit Rate Analysis
- Assessed the relationship between total exits and views per session for the highest-traffic pages to identify where users abandon the site

| Page | Exits | Views per Session |
|------|-------|-------------------|
| `/yeokens/dairy-go-round` | 233,923 | 1.44 |
| `/yeokens/get-banking` | 59,048 | 1.46 |
| `/yeokens/type-a-code` | 32,861 | 1.17 |
| `/yeokens/raffle` | 31,657 | 1.41 |
| `/yeokens/hub` | 25,932 | 1.80 |
| `/yeokens/scan-a-code` | 23,825 | 1.20 |

- `/yeokens/dairy-go-round` is both the highest-traffic and highest-exit page — users complete the game and leave with no onward journey
- Low views-per-session across most pages (1.17–1.46) confirms the site is not successfully cross-linking users to additional content
- `/yeokens/hub` is the strongest page for onward navigation (1.80 views per session) but still has 25,932 exits

## Key Findings
- Yeokens engagement is critically low — only 4.37% of account holders complete the full banking-to-redemption journey, indicating a systemic conversion problem not a traffic problem
- **Transactional pages** (get-banking, spend, raffle) are the strongest performers for engagement depth and return visit rate; gamified pages drive volume but not onward journeys
- **Digital friction** is the primary conversion barrier — form completion rates are near zero (0.01%), and the type-a-code and scan-a-code flows have the lowest views per session of all high-traffic pages
- **Recipes consistently outperform Blogs** across all engagement metrics and show growth in both views and active users; Blogs are declining in active users and engagement time
- **Staff quality** is a genuine differentiator — direct and email channels show strong return user rates, and qualitative review patterns indicate satisfaction with human touchpoints
- The website successfully attracts users to transactional actions but lacks the cross-linking, personalisation, and content discovery features needed to extend the session beyond a single task

## Managerial Recommendations

**`/yeokens/dairy-go-round`**
- Remove the redundant "Play, Win, Enjoy" section and embed it into the post-game pop-up instead
- Introduce cross-linking to recipes, blogs, and rural stays directly on the page to extend the session beyond the game

**`/yeokens/hub`**
- Reposition the "Up for Grabs" voucher section to the top of the page for immediate visibility
- Display all available vouchers filtered by the user's current Yeokens balance to reduce ambiguity and encourage redemption

**Recipes & Blogs**
- Replace vague navigation labels: "Our Food" → "Recipes & Cooking Ideas"; "In the Valley" → "Stories & Blogs"
- Introduce content personalisation — recommend recipes and blog posts based on browsing history and past product engagement
- Strengthen SEO with keyword-optimised titles and structured metadata to improve discoverability via Organic Search
- Build a community hub (e.g. "Yeo & You") where users can submit recipes, leave comments, and build profiles — driving return visits and emotional brand connection


## Tech Stack
- **Language:** Python
- **Libraries:** `pandas`, `numpy`, `matplotlib`, `seaborn`, `openpyxl`
- **Environment:** Google Colab / Jupyter Notebook
- **Data Source:** Google Analytics 4 (GA4) — exported CSV reports
- **Techniques:** Channel segmentation, funnel analysis, bounce/engagement rate benchmarking, content performance comparison, exit rate analysis, cohort-style monthly trend analysis

## How to Run
1. Clone the repo
```bash
git clone https://github.com/GokulKumar-7/yeo-valley-consulting.git
cd yeo-valley-consulting
```
2. Install dependencies
```bash
pip install pandas numpy matplotlib seaborn openpyxl
```
3. Data is provided in the `data/` folder as exported GA4 CSV files — no scraping or API access required
4. Open any notebook in `notebooks/` and run all cells in order
5. Full data tables and pivot analysis are also available in the linked Excel tool (see Appendix)

## Conclusion
This project demonstrates how structured web analytics can transform raw GA4 event data into a clear, prioritised service improvement roadmap for a consumer loyalty programme. Yeo Valley's core problem is not website traffic — it is the near-complete drop-off between account registration and active Yeokens redemption. The analysis consistently points to three root causes: digital friction in transactional flows, a lack of cross-linking between gamified loyalty pages and broader site content, and an underdeveloped content strategy that fails to build return visit habits. Addressing these through targeted UX changes, content personalisation, and community features would directly improve the 4.37% redemption rate and strengthen the Yeokens loyalty programme's long-term commercial value.

