---
date: 2025-06-01
categories:
  - Development
  - Design
  - MkDocs
  - Tutorials
tags:
  - MkDocs
  - CSS
  - Layout
---

# Creating Beautiful Feature Cards

Feature cards are an excellent way to showcase important features or sections of your documentation in a visually appealing way. They look great on landing pages and help users quickly navigate to important content.

<!-- more -->

## Basic Feature Cards

Here's a simple example of feature cards that you can use in your MkDocs Material site:

<div class="grid cards" markdown>

- :fontawesome-brands-html5: __HTML__ 
  
  ---
  
  For content and document structure
  
  [:octicons-arrow-right-24: Learn more](#)

- :fontawesome-brands-js: __JavaScript__ 
  
  ---
  
  For interactive elements and functionality
  
  [:octicons-arrow-right-24: Learn more](#)

- :fontawesome-brands-css3: __CSS__ 
  
  ---
  
  For styling and visual appearance
  
  [:octicons-arrow-right-24: Learn more](#)

- :material-responsive: __Responsive__ 
  
  ---
  
  Works beautifully on all devices
  
  [:octicons-arrow-right-24: Learn more](#)

</div>

## How To Create Feature Cards

Creating feature cards in Material for MkDocs is simple. You need three things:

1. The required markdown extensions in your `mkdocs.yml`
2. CSS styling for the cards (which we've already added)
3. The proper markdown syntax for creating the cards

### Markdown Extensions

Make sure you have these extensions in your `mkdocs.yml`:

```yaml
markdown_extensions:
  - attr_list
  - md_in_html
  - pymdownx.emoji:
      emoji_index: !!python/name:material.extensions.emoji.twemoji
      emoji_generator: !!python/name:material.extensions.emoji.to_svg
```

### Markdown Syntax

The basic syntax for creating feature cards is:

```markdown
<div class="grid cards" markdown>

- :icon-name: __Card Title__ 
  
  ---
  
  Card content goes here
  
  [:octicons-arrow-right-24: Link text](#)

- :icon-name: __Another Card__ 
  
  ---
  
  More content here
  
  [:octicons-arrow-right-24: Another link](#)

</div>
```

## More Complex Example

Here's a more complex example showing cards with different icons and styles:

<div class="grid cards" markdown>

-   :material-clock-fast:{ .lg .middle } __Quick Setup__

    ---

    Set up your documentation site in minutes with simple configuration
    
    [:octicons-arrow-right-24: Installation guide](#)

-   :material-text-box-multiple:{ .lg .middle } __Extensive Documentation__

    ---

    Comprehensive guides and examples for all features
    
    [:octicons-arrow-right-24: Browse docs](#)

-   :material-palette:{ .lg .middle } __Easy Customization__

    ---

    Change colors, fonts, and layouts with simple configuration
    
    [:octicons-arrow-right-24: Styling guide](#)

-   :material-devices:{ .lg .middle } __Responsive Design__

    ---

    Documentation that looks great on any device - desktop, tablet, or mobile
    
    [:octicons-arrow-right-24: Layout options](#)

</div>

## Finding Icons

Material for MkDocs includes thousands of icons you can use in your cards:

- [Material Design Icons](https://pictogrammers.com/library/mdi/)
- [FontAwesome Icons](https://fontawesome.com/icons)
- [Octicons](https://primer.style/octicons/)

Use them with syntax like `:material-account:`, `:fontawesome-brands-github:` or `:octicons-rocket-24:`.

## Card Sizing

You can control the number of columns in your grid by changing the CSS. The default styles adapt to screen size automatically, but you can also create custom CSS rules for specific layouts.

---

Feature cards are a powerful way to enhance your documentation and create a modern, professional look. They're especially useful for landing pages and section overviews. 