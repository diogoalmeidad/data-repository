# Privacy Sandbox

- What is it: Set of features that Google presents as layers of security and protection for user's browser privacy. Acting as a replacement for third-party cookies, they are expected to happen in 2024.
- In Q3 2024 Chrome will start to phase out the 3rd party cookies
- It was postponed to Q1 2025.
- Privacy Sandbox Analysis Tool:
  - Objective: Reduce cross-site tracking while enabling functionalities that keeps online content and services accessible by everyone. 3rd party cookies enable to sign-in, fraud protection, advertising, embed rich third-party content in the website, but also cross-site tracking
 
- There's many purpose-built APIs for specific use cases such as:
  1) Topics API: Browser infers handful of recognizable interest-based categories absed on recent browsing history to help sites to serve relevant ads - the specific sites you visited are no longer shared across the web, unlike with 3rd party cookies
     How it works: API labels each website from a set of recognizable,high-level topics (469 topics, [publicly avaialble](https://github.com/patcg-individual-drafts/topics/blob/main/taxonomy_v2.md)), then browser collects a few of the most frequent topics associated with the websites you've visited. These topics are shared (one new topic per week) with the sites you visit to help advertisers who you more relevant ads, without needing to know the specific website you visited.
     Whenever there's a call to the website, three topics are returned and every week if a user returns to the website, a new topic is learned. There's a 5% chance per-user, per-site, per-epoch (week) random topic is chosen  - the noise is introduced to ensure that it is hard to reidentify the user across sites (if site A sees 'cats' and B sees 'planes', then it's difficult to assess it's the same user), the topics are also shared at different times
  3) Protected Audiences: To build up an audience to show the ad to (remarketing and custom audiences) - there's a buyer which owns an interest group and bids in ad auction:
     a) User enters a website and get's assigned to an interest group
     b) Users visits site displaying ads and an auction takes place on device
     c) Winning ad is displayed
  5)
  6) can be shared across sites to remarket, stored in the device, available for the ad audction. Ask to join ad interest group, 
  7) Attribution Reporting: 
