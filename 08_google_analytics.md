


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

## ✍🏻 What's new
- UA created a new session everytime a user interacted with a new touchpoint (inflated sessions) and GA4 allows to have multiple touchpoints in the same session;
- User acquisition will only look into the first method used to capture the user (first click);
- Traffic acquisition also doesn't report multi-touch journeys but can capture multiple sessions (First last click);
- Under engagement > conversion you will actually be able to see the data-driven impact across multiple sessions (best place to do attribution) -> the challenge is that this only applies for users who conver 


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

 [GA4 Data-Driven Attribution](https://adswerve.com/blog/googles-ga4-data-driven-attribution-model-explained/):
 - First GA4 starts to predict likelihood of conversion, given history of interacting with channels. It will sees the paths that users have taken and see if those paths led to conversion or not and then trains a model that outputs likelihood that a path leads to conversion or not;
 - The algorithm used is Shapley Value. In short, Shapley uses some features and leaves some other out until it has tried every single combination and will output a value that allows to understand how each feature affects the model;
 - Since the data is trained on our GA4's property, the DDA model will be unique to us.
  
  
 ## GA4 Data in BigQuery:
-> Google Analytics doesn't export Google Signals data, therefore event data is different between the platform as Google Signals deduplicates user data (user counts and event counts);
-> Some attribution models like first-click, lineaer, time-decay and position-based in GA4 are going to be deprecated in September, but can be built [on BigQuery](https://www.ga4bigquery.com/how-to-build-your-own-ga4-marketing-attribution-model-comparison-tool-in-bigquery-and-looker-studio/)
 - [GA4 BigQuery documentation](https://developers.google.com/analytics/bigquery?utm_source=convertkit&utm_medium=email&utm_campaign=Useful%20resources%20for%20technical%20marketing%2C%20new%20podcast%20collaboration...%20%E2%80%93%20Simmer%20Newsletter%20%2350%20-%2010069565): Can find here examples of queries
 - [Accesing Nested Variables](https://www.youtube.com/watch?v=B0SG2Q0Jpxg): Data in BigQuery can be stored liked a JSON file with an array of events/user/item properties. To unnest, after the 'FROM' we need to use 'UNNEST(hits) as h" or even "UNNEST(h.product) as p" and then on SELECT either use 'h.' or 'p.'
 
 ## GA4 Tutorials:
 - [Google Analytics official channel](https://www.youtube.com/watch?v=oJx9DpXtmAE&list=PLI5YfMzCfRtZ4bHJJDl_IJejxMwZFiBwz)
 
 ## GA4 in BigQuery Tutorials:
- [Accessing Event, User and Item Data](https://adswerve.com/blog/ga4-bigquery-tips-event-parameters-and-other-repeated-fields-part-two/?utm_campaign=Client_2_23&utm_medium=email&_hsmi=248166973&_hsenc=p2ANqtz-90qyZ3sBHI-657ecdVjCcirfeAl6L7Jd5Cjyl8u1iovQVyJZ_VI-3UbY9Hlx0rKo9SUumONob8NtUQuAmuAuErpyHlhQ&utm_source=newsletter) 
 - [Differences between GA4 and BQ](https://developers.google.com/analytics/blog/2023/bigquery-vs-ui?utm_source=convertkit&utm_medium=email&utm_campaign=Google%20releases%2C%20WebKit%20update...%20%E2%80%93%20Simmer%20Newsletter%20%2352%20-%2010511153): 
   - Active users vs Total Users (Primary user metric in GA4 is Active Users [if it mentions user it is active user and not total users]). To compare with BigQuery we need to filter for active users to compare:
   - HyperLogLog++: GA4 estimates users and sessions using HyperLogLog++ so an unique count is an approximation. In BigQuery we can calculate normally;
   - Latent updates to data: If we have measurement protocol it can take up to 72h to show the data in BigQuery;
   - High cardinality: In GA4 if we have lots of cardinality, it aggregates to 'Others' while in BigQuery we have access to granular data;
   - Google Signals: not in BigQuery like previously mentioned;
   - Data modelling with Consent Mode: GA4 has modellation, while BigQuery doesn't;
   - Session source data: There's first user session source or event level, but not session level in BigQuery;
   - ClientID is an unique identifier based on the 'ga_' 1st party cookie -> when cookies are rejected, privacy_info.analytics_storage and privacy_info.ads_storage is set to 'No', making user_id and user_pseudo_id NULL values;
   - 'collected_traffic' dimensions are event-level data, while 'traffic_source' is user-level data. The former is parsed from the events page_location and page_referrer in an easier format, not relying on cookies;
   - collected_traffic_source is expected to show null values for events where no traffic source dimensions have been observed. A simplified session consists of 5 pageviews and one key event and the user came through a Google Ads campaign. In this case, only the first pageview will actually carry observable campaign information, all other events and key event will not. As an expected result, only the first pageview row in BQ will populate values in the collected_traffic_source dimensions, while pageviews 2-5 and the key event will show null.

 
 ## GA4 Updates:
 - [Conversion counting](https://support.google.com/analytics/answer/13366706?utm_source=convertkit&utm_medium=email&utm_campaign=New+Simmer+course+released%2C+plenty+of+Google-related+news...+%E2%80%93+Simmer+Newsletter+%2353%20-%2010611678): It is now possible to count conversion per event (5 conversions in a session = 5 conversions) and per session (5 conversions in a session = 1 conversion);
 - [Experiments](https://support.google.com/optimize/answer/12979533?utm_source=convertkit&utm_medium=email&utm_campaign=New+Simmer+course+released%2C+plenty+of+Google-related+news...+%E2%80%93+Simmer+Newsletter+%2353%20-%2010611678): It will be possible to connect to different 3rd party tools to perform the experiments and analyse the data in GA4. It will create an audience for both audiences in 'exp_variant_string'
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
