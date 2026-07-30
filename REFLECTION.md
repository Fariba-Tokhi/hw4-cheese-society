# Reflection — HW4

## What did I repeat by hand?

The most obvious repetition was the **shared skeleton**: the `<header>`, `<nav>`, and `<footer>` had to be copied into every single HTML file. Every time I changed a navigation link or updated the footer text, I had to open 8 different files and make the same edit. This was tedious and error-prone — I accidentally broke the relative paths in the `guide/` folder once by forgetting to add `../` before the image paths.

The `<link>` tags to the CSS files also had to be adjusted per page depending on whether the file was in the root or inside `guide/`. This kind of manual path management is exactly the kind of thing a tool should handle.

## What broke when I moved a file?

When I initially organized my files, I moved `guide/index.html` into the `guide/` folder. This broke **all the relative paths** — the CSS links, the image `src` attributes, and the navigation links all needed `../` prepended. The images in the family pages also needed `../images/` instead of `images/`. This taught me that relative paths are fragile and that a static site generator could handle this automatically.

## What would I want a tool to generate for me?

1. **The shared skeleton** — I want to define the header, nav, and footer once and have it injected into every page. A static site generator with partials or layouts would solve this.

2. **Navigation links** — I want a single navigation config that automatically generates the correct `<a>` tags with the right `href` values, regardless of where the page lives in the directory structure.

3. **Asset paths** — I want to reference images and CSS from the root and have the tool rewrite the paths based on the output file's location.

4. **Page metadata** — I'd like to define the `<title>` and `<meta name="description">` in a frontmatter block and have the tool generate the `<head>` for me.

5. **Automatic view-transition-name assignment** — Instead of manually adding `id` attributes and matching `view-transition-name: auto` in CSS, a tool could generate these for me based on the image filename or a simple config.

This assignment made me appreciate the value of templating and static site generators. Doing everything by hand once was educational — but I never want to do it again.