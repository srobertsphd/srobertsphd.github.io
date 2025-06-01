# Feature Cards & Blog Customization Guide

This guide documents the implementation of feature cards and blog customization for this MkDocs Material site.

!!! tip "See Examples"
    Check out the [Feature Cards Examples](feature-cards-examples.md) page to see various types of feature cards in action!

## Feature Cards Overview

Feature cards provide an attractive way to showcase important content in a grid layout. They offer:

- Visual appeal with icons and hover effects
- Responsive design that adapts to screen size
- Flexible content including text, links, and code
- Consistent styling throughout the site

## Implementation Steps

### 1. Enable Required Extensions

First, ensure these extensions are enabled in `mkdocs.yml`:

```yaml
markdown_extensions:
  - attr_list
  - md_in_html
  - pymdownx.emoji:
      emoji_index: !!python/name:material.extensions.emoji.twemoji
      emoji_generator: !!python/name:material.extensions.emoji.to_svg
```

### 2. Add CSS Styling

Add the following CSS to your stylesheet (`docs/assets/stylesheets/blog-custom.css`):

```css
/* Feature Cards Grid Styling */
.md-typeset .grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(16rem, 1fr));
  gap: 1rem;
  margin: 1rem 0;
}

.md-typeset .grid.cards {
  grid-template-columns: repeat(auto-fit, minmax(16rem, 1fr));
}

/* Card Styling */
.md-typeset .grid.cards > ul {
  display: contents;
}

.md-typeset .grid.cards > ul > li,
.md-typeset .grid.cards > li,
.md-typeset .grid > .card {
  border: 0.05rem solid var(--md-default-fg-color--lightest);
  border-radius: 0.5rem;
  padding: 1rem;
  transition: transform 0.25s, box-shadow 0.25s;
  box-shadow: var(--md-shadow-z1);
  margin: 0;
  list-style: none;
}

.md-typeset .grid.cards > ul > li:hover,
.md-typeset .grid.cards > li:hover,
.md-typeset .grid > .card:hover {
  transform: translateY(-0.2rem);
  box-shadow: var(--md-shadow-z2);
}

/* Card Separator Line */
.md-typeset .grid.cards > ul > li > hr,
.md-typeset .grid.cards > li > hr,
.md-typeset .grid > .card > hr {
  margin-top: 0.5rem;
  margin-bottom: 0.5rem;
  display: block;
}

/* Card Icon Styling */
.md-typeset .grid.cards > ul > li > p:first-child > .lg,
.md-typeset .grid.cards > li > p:first-child > .lg,
.md-typeset .grid > .card > p:first-child > .lg {
  font-size: 2.5rem;
  float: right;
  margin-top: -0.5rem;
  margin-bottom: -0.5rem;
}

/* Card Title Styling */
.md-typeset .grid.cards > ul > li > p:first-child > strong,
.md-typeset .grid.cards > li > p:first-child > strong,
.md-typeset .grid > .card > p:first-child > strong {
  font-size: 1.25rem;
  font-weight: 700;
  line-height: 1.6;
  display: block;
  padding-right: 2.5rem;
}

/* Icon Sizing Classes */
.md-typeset .lg {
  font-size: 1.5rem;
  vertical-align: text-top;
}

.md-typeset .xl {
  font-size: 2rem;
  vertical-align: text-top;
}

.md-typeset .xxl {
  font-size: 3rem;
  vertical-align: middle;
}

/* Icon Positioning Classes */
.md-typeset .middle {
  vertical-align: middle;
}

.md-typeset .center {
  text-align: center;
}
```

### 3. Feature Cards Markdown Syntax

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

Key components:
- Container: `<div class="grid cards" markdown>`
- List items: Each card is a list item with icon, title, separator, content, and optional link
- Icons: Use Material Design Icons, FontAwesome, or Octicons
- Title: Bold text with double underscores `__Title__`
- Separator: Horizontal rule `---`
- Link: Optional link at the bottom using Markdown syntax

## Card Variations

### Basic Cards

```markdown
<div class="grid cards" markdown>

- :fontawesome-brands-html5: __HTML__ 
  
  ---
  
  For content and document structure
  
  [:octicons-arrow-right-24: Learn more](#)

- :fontawesome-brands-js: __JavaScript__ 
  
  ---
  
  For interactive elements and functionality
  
  [:octicons-arrow-right-24: Learn more](#)

</div>
```

### Cards with Custom Icon Sizes

```markdown
<div class="grid cards" markdown>

- :material-clock-fast:{ .lg .middle } __Quick Setup__

  ---

  Set up your documentation site in minutes
  
  [:octicons-arrow-right-24: Installation guide](#)

</div>
```

### Cards with Centered Icons

```markdown
<div class="grid cards" markdown>

- :fontawesome-brands-html5:{ .xxl .center } __HTML__

  ---
  
  HTML provides the structure for your web content.

</div>
```

## Blog Customization

In addition to feature cards, we've customized the blog in several ways:

### 1. Enhanced Blog Landing Page

The blog landing page has been customized with feature cards for categories and recent posts:

```markdown
<div class="index-content" markdown>

# Blog

Welcome to my blog!

## Featured Categories

<div class="grid cards" markdown>

- :material-code-tags:{ .lg .middle } __Development__

    ---
    
    Articles about software development.
    
    [:octicons-arrow-right-24: Browse posts](topics/development/)

</div>

## Latest Articles

<div class="grid cards" markdown>

- :fontawesome-solid-calendar:{ .lg .middle } __Article Title__

    ---
    
    Article description.
    
    [:octicons-arrow-right-24: Read more](posts/article-slug/)

</div>

</div>
```

### 2. Modified Blog Plugin Configuration

The blog plugin configuration has been updated in `mkdocs.yml`:

```yaml
plugins:
  - blog:
      blog_dir: blog
      post_dir: "{blog}/posts"
      post_date_format: long
      post_url_format: "{date}/{slug}"
      pagination: true
      pagination_per_page: 5
      # Disable archive and categories in navigation
      archive: false
      categories: false
      # Keep them accessible via URLs
      archive_name: "Past Posts"
      archive_date_format: "yyyy"
      archive_url_format: "archive/{date}"
      categories_name: "Topics"
      categories_url_format: "topics/{slug}"
      categories_toc: false
      # Custom templates
      archive_template: "blog/templates/archive.html"
      category_template: "blog/templates/category.html"
```

### 3. Custom Templates for Archive and Category Pages

Custom templates were created for archive and category pages to improve their appearance:

#### Category Template (`docs/blog/templates/category.html`):

```html
{% extends "blog-meta.html" %}

{% block post_title %}
  <h1>{{ title }}</h1>
  <a href="../.." class="blog-back-button">
    <span class="twemoji">
      {% include ".icons/octicons/arrow-left-24.svg" %}
    </span> 
    Back to Blog
  </a>
{% endblock %}

{% block post_content %}
  {{ content }}
{% endblock %}
```

#### Archive Template (`docs/blog/templates/archive.html`):

```html
{% extends "blog-meta.html" %}

{% block post_title %}
  <h1>{{ title }}</h1>
  <a href="../.." class="blog-back-button">
    <span class="twemoji">
      {% include ".icons/octicons/arrow-left-24.svg" %}
    </span> 
    Back to Blog
  </a>
{% endblock %}

{% block post_content %}
  {{ content }}
{% endblock %}
```

### 4. Additional CSS for Blog Styling

Additional CSS was added to style the blog index, category, and archive pages:

```css
/* Blog index page styling */
.md-typeset .blog > .index-content {
  margin-bottom: 3rem;
  border-bottom: 1px solid var(--md-default-fg-color--lightest);
  padding-bottom: 2rem;
}

/* Blog index separator */
.md-typeset .blog > .index-content + .post:before,
.md-typeset .blog > .index-content + h2:before {
  content: "Recent Posts";
  display: block;
  font-size: 2rem;
  font-weight: 700;
  margin: 2rem 0;
  color: var(--md-primary-fg-color);
}

/* Hide duplicate Recent Posts heading */
.md-typeset .blog > .index-content + h2 {
  display: none;
}

/* Style for auto-generated blog posts on index */
.md-typeset .blog > .post {
  margin-top: 1.5rem;
  margin-bottom: 2.5rem;
  padding: 2rem;
  border-radius: 0.5rem;
  background-color: var(--md-default-bg-color);
  box-shadow: var(--md-shadow-z1);
  border: 1px solid var(--md-default-fg-color--lightest);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

/* Category and Archive Page Styling */
.md-typeset .blog h1 {
  font-size: 2.5rem;
  margin-bottom: 2rem;
  color: var(--md-primary-fg-color);
  border-bottom: 1px solid var(--md-default-fg-color--lightest);
  padding-bottom: 0.5rem;
}

/* Back button for category and archive pages */
.md-typeset .blog .blog-back-button {
  display: inline-block;
  margin-bottom: 2rem;
  padding: 0.6rem 1.2rem;
  background-color: var(--md-primary-fg-color);
  color: var(--md-primary-bg-color) !important;
  border-radius: 4px;
  font-weight: 500;
  text-decoration: none;
  transition: background-color 0.2s ease;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}
```

## Available Icon Sets

Material for MkDocs provides several icon sets:

1. **Material Design Icons**:
   - Prefix: `:material-`
   - Example: `:material-account:`, `:material-home:`
   - [Browse all Material Design Icons](https://pictogrammers.com/library/mdi/)

2. **FontAwesome Icons**:
   - Prefix: `:fontawesome-brands-` or `:fontawesome-solid-`
   - Example: `:fontawesome-brands-github:`, `:fontawesome-solid-user:`
   - [Browse all FontAwesome Icons](https://fontawesome.com/icons)

3. **Octicons** (GitHub's icons):
   - Prefix: `:octicons-`
   - Example: `:octicons-repo-24:`, `:octicons-arrow-right-24:`
   - [Browse all Octicons](https://primer.style/octicons/)

## Using Icon Modifiers

You can modify icons with special classes:

```markdown
:material-icon:{ .lg }             <!-- Larger icon -->
:material-icon:{ .xl }             <!-- Extra large icon -->
:material-icon:{ .xxl }            <!-- Extra extra large icon -->
:material-icon:{ .middle }         <!-- Vertically aligned to middle -->
:material-icon:{ .center }         <!-- Horizontally centered -->
:material-icon:{ .lg .middle }     <!-- Combined modifiers -->
```

## Tips for Feature Cards

1. **Responsive Design**: 
   - Cards automatically adjust to screen size
   - On mobile, they stack vertically
   - On larger screens, they form a grid

2. **Content Flexibility**:
   - Cards can contain any Markdown content
   - Include code blocks, lists, or even images

3. **Hover Effects**:
   - Cards have a subtle elevation effect on hover
   - This creates a clean, modern UI feel

4. **Card Height**:
   - Cards in the same row will have the same height
   - Keep content length relatively consistent for best appearance

5. **Performance**:
   - CSS transitions are hardware-accelerated for smooth effects
   - The layout is optimized for quick rendering

## Complete Example

Here's a complete example of feature cards in action:

```markdown
## Feature Overview

<div class="grid cards" markdown>

- :material-speedometer:{ .lg .middle } __Performance__

    ---
    
    Optimized for speed and efficiency with minimal overhead.
    
    [:octicons-arrow-right-24: Performance tips](#)

- :material-shield-lock:{ .lg .middle } __Security__

    ---
    
    Built with security best practices from the ground up.
    
    [:octicons-arrow-right-24: Security guide](#)

- :material-devices:{ .lg .middle } __Responsive__

    ---
    
    Works beautifully on all devices from mobile to desktop.
    
    [:octicons-arrow-right-24: Layout options](#)

- :material-theme-light-dark:{ .lg .middle } __Theming__

    ---
    
    Easy to customize with light and dark themes.
    
    [:octicons-arrow-right-24: Theme customization](#)

</div>
```

This guide covers all the customizations made to the site, focusing on feature cards and blog enhancements. 