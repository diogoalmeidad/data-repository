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
- 1st party cookies: behalf of website itself | 3rd party cookie: another website like Google places a cookie on your website and then when the user continues to browse the web, those cookies will be available and read there;
- We can create a cookie using a [Custom HTML](https://www.analyticsmania.com/post/cookies-with-google-tag-manager/) or through a Template;
- Through HTML: We could, for example, create a variable that captures a query parameter like the affiliate_id, store in a cookie and then send to GA4. In this case the trigger should be if the page url has the parameter or if the cookie is not undefined. It might be that sometimes the cookie can take a while to be created, so in this case we need to create a Custom Javascript to either return the variable with the cookie value that is capturing the value from the URL or to return the value of the cookie if it has already been created;
- Through Template we can install the 'Cookie Creator' template, in permissions add a new cookie name and create a tag with the cookie name and value (the variable) - need to add the domain starting with '.site.com' to make the cookie available in all sub-domains;
- Use cases: Only fire tag after X amount of actions | block email pop ups to subscribers

## Local Storage // Session Storage
- Can't be shared across subdomains unlike cookies;
- Session storage expires once you close the browser tab while localStorage ( browserStorage) doesn't have an expiration date unless explicitly said. Cookie storage has a manual configuration set;
- It's only client side, server side it's only for cookies;
- You can set a localStorage/Session through the following HTML Code:
 <script> localStorage.setItem('affiliate_id', {{url - affiliate_id}}) </script>
  Where we want to set, what is the value;
- To get the value, create a custom javascript with return localStorage.getItem('affiliate_id') 

## Lookup table (like a Vlookup)
- Allows to not duplicate things;
- Input variable: what is the variable that is going to be evaluated;
- Like if we have two different websites and two different GA4s, the input can be the page hostname and the input will be the different domains while the output will be the GA4 Measurement IDs - then on the GA4 config tag, change the measurement ID to the lookup table;
- All values are exact matches.

## RegEx table (more process heavy compared to Lookup, but more flexible)
- '|' means OR like 'cat|dog+ matches for cat OR dog
- '.' any character like 'ca.t' can match for cart, cast but won't for carper or cat;
- '*' means that the preceeding symbol can exist 0 or multiples times so 'ca*t' can match for ct, cat, caat, caaaaaaaat but won't for cart;
- '.*' means there can be 0 or any number of other characters after 'ca.*t' can match cat, cart, carpet;
- '^' need to start with that so '^mydomain' matches mydomain.com, mydomain.co.uk;
- '$' needs to end with that regex so 'com$' mydomain.com, www.domain.com;
- '\' escapes another regex character, meaning that it removes the power of the symbol so money\$ matches for money$, money$$$ - the $ loses the meaning of having to end with money;
- The logic is the same - there is an input variable that is evaluated and then on the pattern you insert the logic it should look into (regex) and then provides an output;
- We need to go to advanced settings and remove 'full matches only' and 'enable capture groups and replace functionality'

## iFrame Tracking:
- One HTML website is inside another website;
- Problems: can't track actions of iFrame unless we insert the GTM javascript code inside the iFrame | cross-domain tracking can be a problem as 3rd party cookies are being blocked by browsers;
- We need a separate container for the iFrame and install on the website;
- We need to enter preview mode on the website of the iFrame (child) and then enter the parent child and enter debug mode. We enable the debug mode for the child and we will see 2 GTM environments in the debug mode with different symbols to indicate which you are looking into;
- We need to go to GTM Child create a Custom HTML code based on [Simo Ahava's code](https://www.simoahava.com/analytics/cookieless-tracking-cross-site-iframes/) (looks for dataLayer pushes in the iFrame and then sends a postMessage (listener) to the parent page) and edit the parent origin so that the dataLayer pushes from the iFrame is sent to the container of the parent page;
- Then go to the parent page and also add the second Custom HTML code on Simo Ahava's blog (catches postMessages). Now if we preview things, we can now see new events called iframe.gtm.linkClick for example

## Custom Javascript Variables
- Needs to be an anonymous function, needs to return something;
- Accessing elements on the website should be done on DOM Ready, not on container Loaded even though the value might show up there as well - wait until the website document is rendered;
- Be careful with using querySelector if it's a long chain of CSS, because if one thing changes, it will break everything;
- We can use the extension [GTM Variable Builder](https://chrome.google.com/webstore/detail/gtm-variable-builder/feeboihdgpananoagfmbohoogoncndba/related?hl=en)

## Debug:
- To guarantee that the GTM implementation is accurate, see also if variables are ok on Google Analytics event tag to see if the event contains something or is undefined;
- Chrome Developer Tools: **Elements** allows to see the DOM | **Console** allows to check CSS selector and JavaScript errors (see error and if there's a reference to GTM), do a dataLayer push to fire a tag | **Network** tab allows to see which requests are happening - we can filter for example by "google-a" to return all GA requests we can see the status code, for example, to see if the request was accepted | **Application > Cookies ** to see local and session storage and cookies;
- DataLayer inspector: We can go to Console in dev tools and we see some information in green or yellow from Google and that's because of the adswerve extension. If it is brown it means there is an error with that push - we can expand to see the warning. We can also go to Other Analytics and apply it to track facebook events or SS

## GA4 eCommerce Tracking
- Process: The event can be whatever it wants, but it needs to follow a specific structure (eCommerce object), then create a variable that captures the eCommerce item and create custom events to fire on a specific event and then create the GA4 tag alongside the parameters;
- Implementation process: Agree on what we are going to track (which steps will we track in the funnel?), prepare the code snippets and the task description, configure the tags to send the data to GA, then test & debug and launch and monitor;
- For the developers: Recommened to have an eCommerce object with items array. It needs to be consistent, so on view_item and add_to_cart, it needs to have the same parameters. Always needs to send currency, even if it's always the same (ISO Standard). Price as '1.99' or 1.99 doesn't mattter. But it doesn't accept $1.99;
- Check the template [here](https://docs.google.com/document/d/1kuOQP8HSdqEGbs7D0E7wlnr5cvVGRtYOeuUfKd_1zk0/edit) for the different codes for the different events;
- For example, if it is impossible for a developer to know what was the item list name when viewing the item, we can delete the parameter;
- For 'add_shipping_info' we need to put the shipping_tier which is the name of the delivery selected;
- Item-scoped customer dimensions: like payment_type (payment plan?), product_type (bundle?) - can be included in the items array like 'Size' - they don't need to be included in the event parameters, as long as we are sending the items array. Then we can create the CD in GA4 

## Enhanced Conversions
[Introduction to EC](https://adswerve.com/blog/all-you-need-to-know-about-googles-enhanced-conversions/)
- Objective: Model conversions that we can't observe due to privacy settings, technical limitations 
- How: Uses hashed first-party data to recover unobserved conversions by matching with signed-in Google account information. 
- It's not an estimation. They are actual conversions that have happened;
- Implementation: 
  1) On the tag in GTM enable 'include user-provided data from your website';
  2) Create a user-provided data variable and pass the information like email, phone, name, address (it's mandatory to have either email, address or phone number);
  3) Test to see if on GTM you see the Enhanced Conversion Values, alongside Conversion ID and label;
  4) See if a network request was sent and check parameters like 'em' to see if email is being sent;
  5) Check on Google Ads if for that tag under 'Diagnostics' you can see it recording enhanced conversions


## GA4 UserID
- User logs in allows to understand phone with laptop is the same with desktop;
- Need to send UserID to dataLayer like:
  dataLayer.push({
   'event': 'userData', //or login, wtv
   'user_id' : '123abc' // can't be identifiable
  })
- 1) need to create a dataLayer variable with the userId;
  2) Go to GA4 Config Tag - fields to set field name = "user_id" (exactly like this) value = variable;
  3) check if the following events after login have on the config tag the user_id
  4) Go to debug mode and verify if the user_id is there
  5) GA4 in 24h: go to events and add a comparison to see how many logged in with userid;
  6) GA4 in explore: add in the rows the 'app-instance ID' those that look something like 2312312313.12313123 are the ones from GA4 that it creates automatically for those who did not login, the others with different formatting comes from you;
  7) We can also pass on GA4 Config tag on the user properties the user_id and add it as a custom dimension so we can use it on the exploration as well

## Server Side Tracking
[Benefits](https://www.analyticsmania.com/post/introduction-to-google-tag-manager-server-side-tagging/):
- Reduced loading time of page: Because there's only one script loaded and then sent to the server and then there the actual processing takes place (and sending the data to other platforms), leads to a lower loading time since there are not multiple scripts running;
- Control what data is sent to 3rd party entities: With javascript scripts, we are not sure of all data that we are collecting and sending to external entities, but with SS we can specify which data we want to share;
- Reduce the impact of adblockers: Even if users accept the cookies, if they have an adblocker it will block data to be sent to GA. SS domains at the moment are not blocked by adblockers;
- [Temporary] extent duration of cookies: With ITP, cookies on Safari browsers were limited to 7 days. However, with SS, the cookie can be stored there and will live for as long as you define. ATM Apple is working to change this;

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
- [Fundamentals of Server Side](https://developers.google.com/tag-platform/learn/sst-fundamentals?utm_source=convertkit&utm_medium=email&utm_campaign=Some%20excellent%20resources%20for%20technical%20marketing...%20%E2%80%93%20Simmer%20Newsletter%20%2351%20-%2010283594)
