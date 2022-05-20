---
#
# Use the widgets beneath and the content will be
# inserted automagically in the webpage. To make
# this work, you have to use › layout: frontpage
#
layout: frontpage
header:
  image_fullwidth: CorrelAid-Banner.png
widget1:
  title: "Mission"
  url: '/about'
  image: widget-1-302x182.jpg
  text: 'We connect data scientists with organizations that advance the social good.'
  
widget2:
  title: "Getting involved"
  url: '/getting-involved'
  image: widget-1-302x182.jpg
  text: 'Do you want to apply your data science skills to solve a real-world problem? Are you part of an NGO that wants to use data science to operate more efficiently and effectively? Then get in touch!'
  
widget3:
  title: "Events"
  url: '/events'
  image: widget-github-303x182.jpg
  text: 'We are organizing a number of events around data science for the social good.'
#
# Use the call for action to show a button on the frontpage
#
# To make internal links, just use a permalink like this
# url: /getting-started/
#
# To style the button in different colors, use no value
# to use the main color or success, alert or secondary.
# To change colors see sass/_01_settings_colors.scss
callforaction:
 url: https://correlaid.us12.list-manage.com/subscribe?u=b294bf2834adf5d89bdd2dd5a&id=915f3f3eff
 text: Inform me about upcoming projects and events ›
 style: alert
permalink: /index.html
#
# This is a nasty hack to make the navigation highlight
# this page as active in the topbar navigation
#
homepage: true
---

<div id="videoModal" class="reveal-modal large" data-reveal="">
  <div class="flex-video widescreen vimeo" style="display: block;">
    <iframe width="1280" height="720" src="https://www.youtube.com/embed/3b5zCFSmVvU" frameborder="0" allowfullscreen></iframe>
  </div>
  <a class="close-reveal-modal">&#215;</a>
</div>
