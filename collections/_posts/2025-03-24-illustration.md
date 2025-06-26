---
layout: post
title: "Illustration and animation"
date: 2025-03-25
categories: ["Illustration"]
description: "Illustrations, animations, icons, characters and comics."
thumbnail: "/assets/images/gen/blog/blog-illustration-thumbnail.png"
image: "/assets/images/gen/content/blog-illustration/buybay-comic/page1-row1.png"
border: false
client: various clients
---

# BuyBay: icon libraries

BuyBay specializes in taking returned products from webshops, assessing and improving them, and reselling them. To streamline the assessment process, BuyBay developed flexible 'grading' software as a SaaS solution. I created various icons for this software.

### Regular icons

The BuyBay grading software uses the [Lineair icon library](https://linearicons.com) for icons on regular buttons. This library contains 1000 icon images, but that was not enough for all purposes so I had to create several new icons in the same style. Here are some samples. The blue icons are examples from the Lineair icon library, the green icons are my designs.

{% include framework/shortcodes/figures.html
  path="/assets/images/gen/content/blog-illustration/icons/lnr"
  files="0001-home.svg,0014-pencil.svg,0064-umbrella.svg,0151-envelope.svg,0182-file-check.svg,0287-user.svg,0390-calendar-empty.png,null,null"
  padding="10%"
  background_color="#BFE8EB"
  title="Samples from the Lineair icon library"
%}

{% include framework/shortcodes/figures.html
  path="/assets/images/gen/content/blog-illustration/icons"
  files="beluga.svg,bol.svg,pallet.svg,add-pallet.svg,move-lp.svg,clipboard-paste-into.svg,conveyor.svg,null,null|dev.svg,edit-date.svg,info.svg,palm-tree.svg,robot.svg,rules.svg,text.svg,null,null"
  padding="10%"
  background_color="#D3EFCB"
  title="My icons in the same style"
%}

### 3D icons
Options in the BuyBay grading workflows have large buttons, so that they are easy to hit on touch screens. I created dozens of large 3D icons for these buttons. Here are a few samples.

{% include framework/shortcodes/figures.html
  path="/assets/images/gen/content/blog-illustration/grading-icons"
  files="azertyKeyboard.svg,deepClean_true.svg,exceptionReason_emptyPackage.svg|packageState_original_opened_damaged_replace.svg,productStateExpert_not_functional.svg,ukPlug.svg"
  padding="1rem"
  background_color="#D3EFCB"
%}

The icons are easily recognizable as a family, because they share the same perspective. [Read more on the context of these icons](/blog/2025-03-31-grading-visual-design/)

# BuyBay: functional animations

Animations are not just fun; they can be very functional. At BuyBay (a company that resells webshop returns) I solved two UX problems only by adding simple animations.

## Animation to indicate product placement

 In the BuyBay warehouse, incoming products are counted and placed on a conveyor belt. On rare occasions, the counters have to place the product on a cart instead of the conveyor belt. This led to many mistakes because they were so accustomed to using the belt that it had become an automatism. I created different color schemes and animations to indicate the use of the belt or a cart. This solved the problem completely.

{% include framework/shortcodes/figure.html
  src="/assets/images/gen/content/blog-illustration/conveyor-animation.png"
  title="Animation that indicats product placement"
%}

### Easter egg

During holidays, the box in the animations above is occasionally replaced with a thematically appropriate alternative, such as an Easter egg for Easter.

{% include framework/shortcodes/figure.html
src="/assets/images/gen/content/blog-illustration/easter-egg.png"
title="Conveyor belt with chocolate letter, only visible on Sinterklaas (Dutch holiday)"
%}

A few other alternatives for the box:

{% include framework/shortcodes/figures.html
  path="/assets/images/gen/content/blog-illustration/easter-egg"
  files="egg3.svg,pumpkin.svg,box-orange.svg,valentine-present.svg,baklava1.svg"
  background_color="#FAF2C5"
  title="Easter eggs for Easter, Halloween, King's day, Valentine's day and Eid al-Fitr"
%}

## <a name="animation-load-time"></a> Animation to reduce perceived load time

In the BuyBay warehouse, so-called graders assess webshop returns. They have to follow a step-by-step workflow. We received complaints that new steps sometimes took a long time to load, which made the app feel unresponsive. Unfortunately, we could not fix this delay because it came from third-party software. So, I decided to fix the perception; when the user clicks 'Next' or 'Previous', the current step scrolls out of view. This immediate visible response made the application feel faster and solved the problem.

{% include framework/shortcodes/figure.html
  src="/assets/images/gen/content/blog-illustration/grading-transition.png"
  title="Transition animation to reduce perceived load time"
%}

# Quiz and website hosts

From 2000 to 2012, I co-owned a web design agency. For some of the clients, I created animated hosts that accompanied websites or online quizzes.

{% include framework/shortcodes/figures.html
  path="/assets/images/gen/content/blog-illustration"
  files="flits.png,sonja.png,null"
  title="Political reporter Flits and Sonja, the charming assistant of studieweb.nl"
%}

{% include framework/shortcodes/figure.html
  src="/assets/images/gen/content/blog-illustration/simenavi.png"
  title="Water droplets Sim and Avi, hosts of a website  about water for the Simavi foundation"
%}

<script language="javascript">
  let counter = 1;

  function showNext() {
    const elem = document.getElementById("pikwisso");
    counter++;
    if (counter > 5) counter=1;
    elem.src = '/assets/images/gen/content/blog-illustration/pikwisso/pikwisso-spinner.gif';
    elem.onload=() => {
      elem.src=`/assets/images/gen/content/blog-illustration/pikwisso/pikwisso${counter}.png`;
    }
  }
</script>
{% include framework/shortcodes/figure.html
  src="/assets/images/gen/content/blog-illustration/pikwisso/pikwisso1.png"
  id="pikwisso"
  title="Cultural host Piquizzo - one of five animations. <a id='pikwissoLink' style='display: inline;' href='javascript:showNext();'>Show next animation</a>"
%}

# <a name="smoking"></a> Promotion material for a course to stop smoking

In 2017, DSM abolished smoking areas and offered employees a course to quit smoking through my then-employer [MyDailyLifestyle](http://www.mydailylifestyle.com). I was tasked with creating promotional material for this initiative. I came up with the idea of cigarette packs, which were to be distributed in the company's cafeterias. Since it appeared as though free cigarettes were available, the packs effectively caught people's attention. However, upon closer inspection, one could read a recommendation for the course.

{% include framework/shortcodes/figures.html
  path="/assets/images/gen/content/blog-illustration/roken"
  files="roken-voor.jpg,roken-achter.jpg"
  border="false"
  title="Fake sigaret package to promote a course to quit smoking"
%}

# Logo for Laika.nl

From 2000 to 2012, I was a co-owner of a web design and game development agency named [Laika](/blog/2025-03-25-laika-games). The name was inspired by the first animal in space. I designed the logo for the agency.

{% include framework/shortcodes/figures.html
  path="/assets/images/gen/content/blog-illustration"
  files="laika-logo.png,null,null"
  border="false"
  title="Logo for Laika.nl"
%}

# BuyBay: comic

BuyBay specializes in taking returned products from webshops, assessing and improving them, and reselling them through online sales channels. I created a comic that illustrates the company's process.

{% include framework/shortcodes/figure.html
  src="/assets/images/gen/content/blog-illustration/buybay-comic/page1.png"
  border="false"
  title="BuyBay process: page 1"
%}

{% include framework/shortcodes/figure.html
  src="/assets/images/gen/content/blog-illustration/buybay-comic/page2.png"
  border="false"
  title="BuyBay process: page 2"
%}

# Graphic novels

I wrote two graphic novels, De Hemingway triatlon (The Hemingway Triathlon, 2019) and Mao's Mussen (Mao's Sparrows, 2013). I wrote the stories, drew all the pages and I designed the covers (I received some aid from Peter Kuiper for the cover of De Hemingway triatlon).

{% include framework/shortcodes/figures.html
  path="/assets/images/gen/content/blog-illustration/books"
  files="mussen-cover.jpg,hemingway-cover.png"
  title="Covers from <b>Mao's mussen</b> and <b>De Hemingway triatlon</b>"
%}

{% include framework/shortcodes/figure.html
  src="/assets/images/gen/content/blog-illustration/books/page_118.png"
  title="Page from De Hemingway triatlon"
%}
