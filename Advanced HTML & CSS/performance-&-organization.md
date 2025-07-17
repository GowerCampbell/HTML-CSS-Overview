# Performance & Organization

How do we design the right structure for a code base and identify all the diiferent components that work together, how do we speed up production and make a better experience?

## Strategy & Structure
Where developing the code base, building a strong directory architecture, outlining design patterns and how to find ways to reuse common code?

### Style Architecture
What type of styles can we create based on intent, which include creating directories for a common base styles, user interface components and business logic modules?

Base (comon styles & variables used across the entire website)
-normalize.css
- layout.css
- typography.css

Components (User Interface Elements)
- alerts.css
- buttons.css
- forms.css
- nav.css
- tables.css

Modules (Business Needs)
- aside.css
- footer.css
- header.css

Why do we start thinking of websites as systems than individual pages?

How is it important that the modules contain styles that are specfic to business logic? 

When using different components to mark up a HTML how dows the seperation of style encourage the well thought out presets and the ability for styles to be widely shared and reused?

Researching CSS methodologiies such as object oriented css(OOCSS) or Scalable and Modular Architecture for CSS, (SMACSS)

## Object Oriented CSS
Created by Nicole Sullivan
Link: https://oocss.org/about-us (CSS Code Wars)
- Separate Structure from skin
- Separate Content from container

By allowing styles to be inherited and displayed without conflict, how do we go about abstracting the layout of an element from the theme of a website?
- In using a solid grid and layout structure, along with well crafted modules.

By seperating content from the container do we remove the dependency of a parent element by nesting children?
- Elements need to inherit default styles that can be extended with multiply classes.

HTML
<div class="alert alert-error">
  <p class="msg">...</p>
</div>

CSS
.alert {...}
.alert-error {...}
.msg {...}

Remember Object orinted CSS advocates building a componenet libary, staying flexible and utitlizing a grid?

## Scalable & Modular Architecture for CSS
Developed by Jonathan Snook
Link: https://smacss.com/
Breaking up styles into five core catogories:
- Base (Core elements: general defaults)
- Layout (Sizing and grid styles of different elements)
- Module (Targeted elements of the page such as navigation or feature styles)
- State (Augment or Override other styles includes an alternate state for instance an actived tab)
- Theme (Styles based around the skin, look and feel)

HTML
<div class="alert is-error">
  <p>...</p>
</div>

CSS
.alert {...}
.alert.is-error {...}
.alert p {...}
.alert.is-error p {...}

Remember: alert class falls into the module category while is-error falls into the state category both are then inherit from the layout, base and theme.

## Choosing a Methodology
Link: https://www.viget.com/articles/css-squareoff/











