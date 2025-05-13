---
layout: post
title: "BuyBay: software to announce returns"
date: 2025-03-30
authors: ["Mike Vance"]
categories: ["Wireframes", "Ruby on Rails", "Front end development", "Wireframes", "Visual design"]
description: User friendly website for webshops to announce returns to the BuyBay warehouse.
thumbnail: "/assets/images/gen/blog/blog-3-thumbnail.png"
image: "/assets/images/gen/content/blog-3/visual-design/home.png"
---

# Introduction
BuyBay specializes in taking returned products from webshops, assessing and improving them, and reselling them through online sales channels like eBay. The webshops (called ‘partners’ in this context) announce their products to BuyBay in advance, by uploading an excel sheet with a certain format. The existing software to do that had several usability problems, so I made a redesign.

### My role
- Interviews with webshop holders (together with the product owner)
- Wireframe design
- Visual design
- Implementation of a proof of concept in React

# Analysis
From the BuyBay Operations department and the users we heard the following complaints:
- The Excel file was processed asynchronously. Not all users understood that they had to wait to see if their announcement was accepted.
- If there were errors in only one row (one return), they had to upload the whole file again, and wait again.
- The Excel file had to be formatted correctly, for example prices had to be inside a numeric field, not inside a string field. There was an Excel template that had to be used with correct formatting. Users copy/pasted information into the Excel sheet, changing the formatting of the spreadsheet values. The system often did not accept the changed format, and not all users understood how to fix this.

### Technical analysis
Because the asynchronous processing was so unfriendly to the users, I investigated if we could change this in a synchronous process. I looked for the largest files available and checked the processing time in the back end. My conclusion was that it could be done.
Also I found a node module that could read Excel files, so front end processing was perhaps possible as well.

# Synthesis / wireframes

I made a redesign where the user receives immediate feedback after upload. It is very tolerant on formatting (everything is converted to a string first). If there are still errors left, the the user can change those rows only, without having to upload the whole file again.

Here are a the most important screenshots from the wireframes:

{% include framework/shortcodes/figure.html src="/assets/images/gen/content/blog-3/wireframes/flowchart.png" title="Flowchart" %}

{% include framework/shortcodes/figure.html src="/assets/images/gen/content/blog-3/wireframes/announce1.png" title="Announce a batch of returns - step 1" %}

{% include framework/shortcodes/figure.html src="/assets/images/gen/content/blog-3/wireframes/announce-uploading.png" title="Announce a batch of returns - feedback" %}

{% include framework/shortcodes/figure.html src="/assets/images/gen/content/blog-3/wireframes/announce2.png" title="Announce a batch of returns - errors found in the Excel file" %}

{% include framework/shortcodes/figure.html src="/assets/images/gen/content/blog-3/wireframes/announce-validating.png" title="Announce a batch of returns - validating the fixes of the errors" %}

{% include framework/shortcodes/figure.html src="/assets/images/gen/content/blog-3/wireframes/announce-feedback.png" title="Announce a batch of returns - success message" %}


# Visual design
When the wireframe design was accepted, I created the visuals:

{% include framework/shortcodes/figure.html src="/assets/images/gen/content/blog-3/visual-design/announce1.png" title="Announce a batch of returns - step 1" %}

{% include framework/shortcodes/figure.html src="/assets/images/gen/content/blog-3/visual-design/announce-validating.png" title="Announce a batch of returns  - feedback" %}

{% include framework/shortcodes/figure.html src="/assets/images/gen/content/blog-3/visual-design/item-errors.png" title="Announce a batch of returns - errors found in the Excel file" %}

{% include framework/shortcodes/figure.html src="/assets/images/gen/content/blog-3/visual-design/item-errors-fixing.png" title="Announce a batch of returns - validating the fixes of the errors" %}

{% include framework/shortcodes/figure.html src="/assets/images/gen/content/blog-3/visual-design/creating-announcement.png" title="Announce a batch of returns - feedback" %}

{% include framework/shortcodes/figure.html src="/assets/images/gen/content/blog-3/visual-design/announcement-done.png" title="Announcement complete" %}


# Implementation
I created a proof of concept in React to see if it was possible to do the validation of the Excel file in the front end, before it is uploaded to the server. This turned out to be doable and the we decided to build the application in React.

# Later improvements
Later improvements include statistics, a homepage that offers the latest updates and a calendar and a list view where you can see your own announcements.

{% include framework/shortcodes/figure.html src="/assets/images/gen/content/blog-3/visual-design/home.png" title="Homepage with statistics" %}

{% include framework/shortcodes/figure.html src="/assets/images/gen/content/blog-3/visual-design/deliveries.png" title="Deliveries consisting of multiple themed 'batches'" %}

{% include framework/shortcodes/figure.html src="/assets/images/gen/content/blog-3/visual-design/calendar.png" title="Calender view of the deliveries" %}

{% include framework/shortcodes/figure.html src="/assets/images/gen/content/blog-3/visual-design/items.png" title="Overview of all items exported to BuyBay" %}




# Result
With the new software in place, the BuyBay Operations department encountered hardly any upload problems for webshops anymore.
