+++
date = '2025-07-27T15:00:41+01:00'
draft = false
title = 'Job Search Optimisation automation using n8n'
+++
Searching for roles can be very time-consuming especially when the job title you're searching for is a common one which applies to a wide variety of domains such as my job title does.  

Using my n8n automations skills and my knowledge of GenAI, I built 3 automations to save time and focus my job search.  The first automation saves me around 2 to 3 hours of reading job roles

## Summarising (GenAI) and keyword search - triggered by a webhook
The first automation us triggered by a webhook to which is sent the URL of a role (usually from LinkedIn).  Any roles that are processes by the automation are stored in a Google Sheet.  Using the URL that triggered the automation as the unique key, the sheet is searched to see if the URL has already been processed and if it has, the automation stops there.
If, however, the url is not already in the spreadsheet, the web page for the role is retrieved passed through to OpenAI for analysis and the analysis is stored in the same Google Sheet.

To trigger the workflow, as I view the headlines and first paragraph or 2 of a role on LinkedIn (and others), I need to be able to send the role to the webhook.  To do this I have a browser extension which allows me to right-click on a URL and select "send to webhook" in the drop-down.

## Excluding and filtering contract roles from an RSS feed
The 2nd automation consumes an RSS feed on a schedule.  Once again Google Sheets - two of them - are used to track things.  The first sheet lists the RSS feed URLs and the name I gave that feed.  These are retrieved and passed to the "read RSS feed" which captures all the roles for each of the feeds.  A small piece searches for terms in the job title which are not of interest (e.g. I exclude "developer" as these roles are not relevant to me).
A filter on the excluded flag stops the processing of those records but lets through all the other roles.  An information extractor node uses AI to find and extract key information such as the day rate, whether the role's text has the words automation or observability, etc.
A 2nd filter check if these terms are present and if they are adds the role to a Google Sheet.
This automation has reduced the number of roles I need to read from around 50 per day to a handful.

