# Google Tag Manager

## Server Side Tracking
[Benefits](https://www.analyticsmania.com/post/introduction-to-google-tag-manager-server-side-tagging/):
- Reduced loading time of page: Because there's only one script loaded and then sent to the server and then there the actual processing takes place (and sending the data to other platforms), leads to a lower loading time since there's not multiple scripts running;
- Control what data is sent to 3rd party entities: With javascript scripts we are not sure of all data that we are collecting and sending to external entities, but with SS we can specify which data we want to share;
- Reduce impact of adblockers: Even if users accept the cookies, if they have an adblocker it will block data to be sent to GA. SS domain at the moment are not blocked by adblockers;
- [Temporary] extent duration of cookies: With ITP, cookies on Safari browsers were limited to 7 days. However with SS, the cookie can be stored there and will live for as long as you define. ATM Apple is working to change this;

[New data Flow](https://www.simoahava.com/analytics/server-side-tagging-google-tag-manager/):
- Processes are initialized by incoming HTTP requests;
- Requests are digested by clients (GA4, UA);
- Client parses the request, generates event data object (event name) that is used by tags to send the data to their endpoints (Facebook, Google Ads, etc.) [outgoing HTTP requests]

## Initiatives
[Soteria Project](https://github.com/google/gps_soteria):
- Allows to send the profit through server side by using Firestore and SSGTM;
- Firestore is a NoSQL document database that has a native connector (template) to SS GTM;
- SS GTM then will read the document that stores the SKU profit;
- After this, SS GTM will send either through Measurement Protocol the profit to Google Analytics or through encrypted Conversion Value to Google Ads (floodlights not available yet);
- We can store the profit by storing on the cloud the CSV or by storing the profit on BigQuery and then sending to Firestore.

## Tutorials
- [Fundamentals](https://developers.google.com/tag-platform/learn/sst-fundamentals?utm_source=convertkit&utm_medium=email&utm_campaign=Some%20excellent%20resources%20for%20technical%20marketing...%20%E2%80%93%20Simmer%20Newsletter%20%2351%20-%2010283594)
