---
layout: note
title: Mobile Pages
---

### Mobile Pages ###

The viewport is the window through which you view the page's content. It constrains the height and width of the html element, the page's top level element.

Since most sites are designed for the desktop, mobile devices use a larger viewport (iOS uses 980px) and scale the page down. If we're optimizing the page for mobile sites, we can tell the browser not to do this with a meta viewpoint tag:

{:lang='html'}
~~~
<meta name="viewport"
    content="width=device-width, initial-scale=1" />
~~~

So the viewport is set to the device's width and not scaled. Now, according to the principles of responsive design, we design the page for mobile and then add style for the desktop.

To isolate desktop environments, we use media queries:

{:lang='html'}
~~~
<link href="main.css" media="screen, handheld"
    rel="stylesheet" type="text/css" />
<link href="desktop.css" media="screen and (min-width: 540px)"
    rel="stylesheet" type="text/css" />
~~~

Since IE 8 and below don't support media queries, we can use the following workaround to load the desktop style in older IE browsers (which are all desktop browsers).

{:lang='html'}
~~~
<!--[if (lt IE 9)&(!IEMobile)]>
<link href="desktop.css" rel="stylesheet" type="text/css" />
<![endif]-->
~~~

The desktop style can override properties in the mobile style. For exmaple, to stretch a content div across the whole screen on mobile but cap its width on the desktop, we can use the following in our mobile style:
  
{:lang='css'}
~~~
#content {
  width: 100%;
}
~~~

Then we override it in the desktop style:

{:lang='css'}
~~~
#content {
  width: 540px;
}
~~~

You can see this technique on my [landing page](https://github.com/theandrewdavis/theandrewdavis.github.com).

### References ###

* [HTML5Rocks: Creating a Mobile-First Responsive Web Design](http://www.html5rocks.com/en/mobile/responsivedesign/)
* [Apple: Configuring the Viewport](https://developer.apple.com/library/safari/#documentation/AppleApplications/Reference/SafariWebContent/UsingtheViewport/UsingtheViewport.html)
* [Mozilla: Using the viewport meta tag to control layout on mobile browsers](https://developer.mozilla.org/en-US/docs/Mobile/Viewport_meta_tag)
