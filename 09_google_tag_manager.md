# Google Tag Manager

## Tips
- Accessing something within an object like 'userAttributes: {country: 'United States'}' needs to be userAttributes.country - each level is separated with a dot;
- Accessing values within an array: like 'transactionProducts [{sku:'DD44'}, {sku:'DD44'}] to get the SKU of the second product, need to specify which object we want to see transactionProducts.1.sku;
- We can't create a datalayer variable to capture all parameters of each array, but there are some codes to get all (in Bonus)
- 'Message' means that the dataLayer push was missing the 'event' key. You can still see which variables would have information, but can't fire tags on it;
- Be aware of when the Customer ID is sent and the trigger that we use for it;
- Auto-event variable requires interaction from the user, DOM element variable doesn't;
- Container Loaded = Page View - GTM Snippet is loaded (gtm.js) | DOM Ready is when the browser has rendered the HTML file it gets from the server and creates DOM (gtm.dom)| Window Loaded when everything is loaded (gtm.load);
- Firing and exception need to happen on the same event, so we can't put for example firing on gtm.js and exception on gtm.load;
- Tag sequencing ignores exceptions as sequencing has higher priority;
- Priority doesn't lead directly to be fired first as it also depends on how heavy is the tag. It just changes the order that they are executed.

## [CSS Selectors](https://www.simoahava.com/gtm-tips/10-useful-css-selectors/)
- If we do something like '.red-button', it means we are targeting the class of red-button;
- If we do something like '#important', it means we are targeting the ID of important;
- If we do something like 'a', it means we are targeting all the elements 'a';
- If we do something like '.main > .red-button', we are targeting an element that has a class red-button which is a direct child of another element that has the class main;
- If we do something like '.main.red-button', we are targeting a class that has a blank space that should not be there 'class=main red-button';
- If we do something like '.green a', we are looking for the links of the blocks (link elements are 'a') that are anywhere under the green class;
- To trigger based on this, it needs to be 'Click Element';
- Wildcare CSS Selector: If we do something like 'button.one, button.two *' we are targeting either the button with class one or the button with class two and everything below them;
- To test: Go to console and enter document.querySelectorAll('');
- [To learn CSS](https://flukeout.github.io/)

## Cookies
- Pieces of information that website stores on the browser like to identify user;
- 1st party cookies: behalf of website itself | 3rd party cookie: another website like Google places a cookie on your website and then when the user continues to browse the web, those cookies will be available and read there.

## Custom Javascript Variables
- Needs to be an anonymous function, needs to return something;
- Accessing elements on the website should be done on DOM Ready, not on container Loaded even though the value might show up there as well - wait until the website document is rendered;
- Be careful with using querySelector if it's a long chain of CSS, because if one thing changes, it will break everything;
- We can use the extension [GTM Variable Builder](https://chrome.google.com/webstore/detail/gtm-variable-builder/feeboihdgpananoagfmbohoogoncndba/related?hl=en)

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

[Transformations](https://developers.google.com/tag-platform/tag-manager/server-side/transformations?hl=en)
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
