---
layout: post
title: "BuyBay: predictable product routing"
date: 2025-03-29
authors: ["Dirk-Jan Hoek"]
categories: ["Wireframes", "Visual design", "Front end development", "Ruby on Rails"]
description: Webshop returns are routed in the BuyBay warehouse based on rules. I enhanced this system for better predictability and adaptability.
thumbnail: "/assets/images/gen/blog/blog-4-thumbnail.png"
image: "/assets/images/gen/blog/blog-4-large.png"
weight: 1
---


# Introduction

BuyBay takes returned products from webshops (called ‘owners’ from now on), assesses and improves them, and sells them on online sales channels. When returns arrive in the BuyBay warehouse, employees (‘counters’) scan these products to verify if they are the same as the webshop announced to BuyBay. After confirming a product, it has to go to a certain location. For example products with data go to a department where the data is wiped.

{% include framework/shortcodes/figure.html src="/assets/images/gen/content/blog-4/old-rules.png" title="List of counting rules" %}

To determine this routing, the BuyBay software contains ‘rules’. Every rule consists of criteria like brand, product price and owner (the webshop). It also contains a destination, like the aforementioned wiping department.

{% include framework/shortcodes/figure.html width="50%" src="/assets/images/gen/content/blog-4/edit-rule.png" title="Form to edit a rule" %}

When a product is scanned, all the rules in the table are evaluated from top to bottom. As soon as a matching rule for a product is found, its destination is enforced. Usually, a conveyor then brings the product to the right position in the warehouse. The prioritisation of the rules is automatic, the algorithm for it is too complex to explain here.

When a new owner joins BuyBay, it often needs new or updated rules. It is hard to configure this because:

- You can set up dedicated rules for the new owner, but there may be unwanted rules with a higher priority that catch the product first.
- You can not change the order of the rules by yourself, it is determined by an algorithm.
- When you change an existing rule, you may accidentally change the routing of products from other webshops. It is hard to predict the effect of your changes.
- There a more then 200 rules. There is no overview and often new ones are created, while it is not needed. Nobody dares to erase rules and it is not visible whether a rule is used or not. A lot of rules can theoretically be combined into one, but that is hard to do.
- There is no preview of how the rules will work out for a new webshop.

### My role

- Wireframe designs
- Visual designs
- Implementation of the hardest part in Ruby on Rails

> "The new counting rules have improved the setup of our flows. No longer do we encounter questions about how the logic works and how we can ensure that one rule takes precedence over another.”

# Concepts

I created a number of ideas, I only present the selected concept here. In this concept each owner has its own rules. But if no matching rule is found, the system will look inside the generic rules, that apply to all owners.

For each owner a flow chart is generated based on its rules:

{% include framework/shortcodes/figure.html src="/assets/images/gen/content/blog-4/wireframes/owner-preview.jpeg" title="Generated flow chart for an owner" %}

The flow chart also shows the generic rules, so that you have the full picture here. This view makes it much easier to see what happens to products from this owner.

When you click ‘Edit’, you see an ‘edit’ view:

{% include framework/shortcodes/figure.html src="/assets/images/gen/content/blog-4/wireframes/edit-owner-rule.png" title="Generated flow chart for an owner" %}

There is no automatic ordering anymore, the rules can be dragged and dropped. With the pencil icon, you can edit a particular rule. This leads to the form shown before:

{% include framework/shortcodes/figure.html width="50%" src="/assets/images/gen/content/blog-4/wireframes/edit-rule-form-top.png" title="Form to edit owner rule" %}

The stakeholders were very happy with this solution, so I continued with a visual design.

# Visual design

{% include framework/shortcodes/figure.html src="/assets/images/gen/content/blog-4/visual-design/preview.png" title="Generated flow chart for an owner" %}

{% include framework/shortcodes/figure.html src="/assets/images/gen/content/blog-4/visual-design/sort-owner-rules.png" title="Visual design of the sorting page" %}

# Implementation
Next I created the ‘stories’ (tasks) for implementation. I picked up the task for the automatically generated flowchart preview myself. I considered two approaches:

- SVG rendering
- Generating CSS in the back end

I decided the last option was the simplest and created a proof of concept. This worked well and then I did the real implementation. It basically works like this:

- I created a service class `RowsBuilder` that prepares an array of rows. This is an abstract version of the flowchart. Each row is a hash of properties, like these:

    - Y-position, can be 0,1, 2 etc.
    - Attributes (the criteria on the left side)
    - Destination (what you see behind the arrow)
    - Whether the row is connected to a ‘parent’ that has the same destination, if so, the y-position of that row. This is used for the vertical lines that connect the horizontal ones in the flowchart.
    - If there is a parent, the x-position of the connector, can be 0, 1, 2 etc.

- I created a presenter class `FlowchartRowPresenter` that contains all the logic to convert the abstract rows to  HTML attributes. For example it can generate:
    - the the right class name for the row
    - the ‘style’ attribute for each row that includes its absolute x- and y-position

- I created a controller that generates all the rows with the `RowsBuilder` and converts them into presenters. These are handed over to the view.

# Result

At the time of writing, the new rules have just gone into production. I asked Rick Gerrits, BuyBay operations manager, if he is satisfied. His reply: “The new counting rules have improved the setup of our flows. No longer do we encounter questions about how the logic works and how we can ensure that one rule takes precedence over another. With the new setup, you can easily drag the rule and determine the desired priority as a user. The fact that this can be done per partner is ideal, as it allows us to apply different logics to meet the partner's needs.”

Here is a screenshot from the production website, from the owner with the most complex routing. As you can see it is pretty close to the design (except for an annoying glitch that I would love to improve: the first vertical green line is too close to its left neighbour):

{% include framework/shortcodes/figure.html src="/assets/images/gen/content/blog-4/production-rules.png" title="Counting rule flowchart in production" %}
