# 1. Types of Ad Auctions
## 1.1 First-Price Auction
- The highest bidder pays their own bid.
- Pros: Simple, transparent.
- Cons: Leads to bid shading, where advertisers lower their bids to avoid overpaying.
## 1.2 Generalized Second-Price (GSP) Auction
- Each advertiser pays the next highest bid + a small increment.
- Example:
```bash
Bids: A = $5, B = $4, C = $3
A pays $4.01, B pays $3.01, C pays the minimum bid
```
- Used by Google Ads for search ranking.
- Strategic implication: Not truthful (advertisers might still bid lower to reduce costs).
## 1.3 Vickrey-Clarke-Groves (VCG) Auction (Truthful Auction)
- A type of second-price auction where advertisers pay the harm they cause to others.
- Truthful bidding is the dominant strategy (no incentive to lie).
- Used in Facebook Ads and some Google Display Ads.
## 1.4 First-Price vs. Second-Price Hybrid Auctions
- Many modern ad platforms (Amazon, TikTok, LinkedIn) use a hybrid of first-price and second-price auctions.
- Some platforms now use first-price auctions with bid shading algorithms.

# 2. Key Concepts in Ad Auctions
## 2.1 Ad Ranking and Quality Score
- Bids alone don’t determine ad ranking. Ad relevance and expected user engagement matter.
- Formula for Ad Rank:\
Ad Rank = Bid × Quality Score
- Quality Score considers:
  - CTR (Click-Through Rate) – likelihood users click the ad.
  - Ad Relevance – how well the ad matches the user query.
  - Landing Page Experience – does the page load fast, provide useful content?
## 2.2 Reserve Pricing (Minimum Bid)
- Platforms set a minimum price to ensure advertisers don’t get ads too cheaply.
- Dynamic reserve pricing adjusts based on auction competition.
## 2.3 Bid Shading (First-Price Auctions)
- Since first-price auctions can cause advertisers to overpay, platforms use bid shading algorithms to reduce bids.
- Example:
  - Bid: $5
  - Expected Winning Price: $3.50
  - Platform suggests bidding $3.75 instead of $5.
 
# 3. Bidding Strategies
Advertisers can use different strategies based on their goals (e.g., clicks, conversions, revenue).

## 3.1 Manual Bidding
Advertisers set bids manually based on their expected return on investment (ROI).
## 3.2 Automated Bidding (Machine Learning-Based)
Platforms use ML models to automatically adjust bids for optimal results.\
Common strategies:

- Cost Per Click (CPC) Optimization
  - Goal: Maximize clicks within a budget.
  - Bids are adjusted based on expected CTR.
  - Example: Google’s Enhanced CPC (ECPC).
- Cost Per Acquisition (CPA) Optimization
  - Goal: Get more conversions (e.g., sign-ups, purchases) at a set cost per action.
  - ML models predict conversion probability and adjust bids.
- Return on Ad Spend (ROAS) Optimization
  - Goal: Maximize revenue while keeping ad costs low.
  - Example: Google Smart Bidding uses value-based bidding to maximize revenue per dollar spent.
# 4. Measuring Ad Auction Performance
To evaluate and optimize ad auctions, platforms track:
- CTR (Click-Through Rate): Percentage of users clicking the ad.
- CVR (Conversion Rate): Percentage of clicks leading to a sale/sign-up.
- Ad Fill Rate: Percentage of available ad slots filled with ads.
- Revenue Per Mille (RPM): Revenue per 1,000 impressions.
- Incrementality Testing: Measures how many conversions wouldn’t have happened without ads
