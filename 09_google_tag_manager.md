# Google Tag Manager

## Tips
- Accessing something within an object like 'userAttributes: {country: 'United States'}' needs to be userAttributes.country - each level is separated with a dot;
- Accessing values within an array: like 'transactionProducts [{sku:'DD44'}, {sku:'DD44'}] to get the SKU of the second product, need to specify which object we want to see transactionProducts.1.sku;
- We can't create a datalayer variable to capture all parameters of each array, but there are some codes to get all (in Bonus)
- 'Message' means that the dataLayer push was missing the 'event' key. You can still see which variables would have information, but can't fire tags on it;
- Be aware of when the Customer ID is sent and the trigger that we use for it;

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

##[Transformations](https://developers.google.com/tag-platform/tag-manager/server-side/transformations?hl=en)
- For control over what event parameters is sent to which tag;
- Allows to share what is explicitly defined, augment event parameters by creating rules to edit or add event data (like adding margin data), redact incoming information by excluding event parameters from tags;
- If we select to allow parameters, all non explicitly mentioned parameters are excluded 

## Initiatives
[Soteria Project](https://github.com/google/gps_soteria):
- Allows to send the profit through server side by using Firestore and SSGTM;
- Firestore is a NoSQL document database that has a native connector (template) to SS GTM;
- SS GTM then will read the document that stores the SKU profit;
- After this, SS GTM will send either through Measurement Protocol the profit to Google Analytics or through encrypted Conversion Value to Google Ads (floodlights not available yet);
- We can store the profit by storing on the cloud the CSV or by storing the profit on BigQuery and then sending to Firestore.

## Server Side GTM and GA4
- Benefits:
  1) If we use GA4 through SS GTM we can strip the IP Address before sending to Google, ensuring compliance with GDPR. We can use Server Side GTM Visitor-Region variable to determine the user location based on the IP instead of sending this information to the US;
  2) We don't need to share Measurement ID with end users, thus reducing chance of spammy traffic and enhancing data accuracy;
  3) We can filter hits from countries from where our services are not offered using sGTM Region variable;
  4) We can modify the purchase value of GA4 purchase event like the margin data without end-user knowing.

## Tutorials
- [Fundamentals](https://developers.google.com/tag-platform/learn/sst-fundamentals?utm_source=convertkit&utm_medium=email&utm_campaign=Some%20excellent%20resources%20for%20technical%20marketing...%20%E2%80%93%20Simmer%20Newsletter%20%2351%20-%2010283594)
