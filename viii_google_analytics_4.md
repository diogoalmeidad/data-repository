


<h2> Table of Contents </h2>
<ol>
<ol dir="auto">
<li>Google Analytics 4
<ol dir="auto">
<li>Google Signals</li>
<li>Google Analytics Bidding</li>
<li>Custom Events/Metrics/Dimensions</li>
<li>Measurement Protocol</li>
<li>Consent Mode</li>
<li>GA4 Data in BigQuery</li>
</ol>
</li>

## ✍🏻 Concept Introductions 
 [Google Signals](https://infotrust.com/articles/google-signals-in-google-analytics-4-audience-strategy/): Collect cross-device data from users signed into a Google account. Allows reports on demographics data, cross-device reporting, cross-device remarketing and cross-device conversion exports to Google Ads. On audience creation, allows to use user-data to expand filtering
  Use Cases:
  - Remarketing with more touchpoints (and more devices for same user);
  - Cross device ad spent;
  - Understand cross-device journey;
  <br>
  
  [Reporting Identities](https://www.datadrivenu.com/reporting-identity-ga4/): User ID > Google Signals > Device ID > Modeling
  - User ID: Unique ID when user logs in to assign same user across devices/browsers (need to be set up by us); 
  - Google Signals: Users who signed in to Google account and agreed to share this data;
  - Device ID: Client ID (first party cookie, stored for two years)
  - Modeling: Models behaviour of users who did not accept cookies
  
 - [Google Analytics Bidding] <br>
 - [Custom Events/Metrics/Dimensions] <br>
 - [Measurement Protocol] <br>
 - [Consent Mode] <br>
  
  
 ## GA4 Data in BigQuery:
-> Google Analytics doesn't export Google Signals data, therefore event data is different between the platform as Google Signals deduplicates user data (user counts and event counts);
-> Some attribution models like first-click, lineaer, time-decay and position-based in GA4 are going to be deprecated in September, but can be built [on BigQuery](https://www.ga4bigquery.com/how-to-build-your-own-ga4-marketing-attribution-model-comparison-tool-in-bigquery-and-looker-studio/)
 - [GA4 BigQuery documentation](https://developers.google.com/analytics/bigquery?utm_source=convertkit&utm_medium=email&utm_campaign=Useful%20resources%20for%20technical%20marketing%2C%20new%20podcast%20collaboration...%20%E2%80%93%20Simmer%20Newsletter%20%2350%20-%2010069565): Can find here examples of queries
 
 ## GA4 Tutorials:
 - [Google Analytics official channel](https://www.youtube.com/watch?v=oJx9DpXtmAE&list=PLI5YfMzCfRtZ4bHJJDl_IJejxMwZFiBwz)
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
