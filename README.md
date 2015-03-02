# DBG Frontend Coding Standards. (HTML)

Before you start, do you know why coding standards matters?
>It is just because every line of code should appear to be written by a single person, no matter the number of developers or contributors. So please make sure you follow all the instructions mentioned below.

## SET UP ENVIRONMENT
> Your code editor is your main development tool. you use it to write and save lines of code. Write better code faster by learning your editor's shortcuts and installing key plugins. We encourage using code editors like

- [Sublime](http://www.sublimetext.com/)
- [Atom](https://atom.io/)
- [Brackets](http://brackets.io/)

As a part of our workflow, we use sublime text as our editor of choice. [Click here](https://developers.google.com/web/fundamentals/tools/setup/editor?hl=en) to know more about setting up sublime text with ease.

## Editorconfig

The .editorconfig file is provided in order to encourage and help you maintain consistent coding styles between different editors and IDEs.

By default, .editorconfig includes some basic properties that reflect the coding styles from the files provided by default, but you can easily change them to better suit your needs.

In order for your editor/IDE to apply the properties from the .editorconfig file, you will need to install a plugin.

For more details, please refer to the [EditorConfig](http://editorconfig.org/) project.

## Note
__Please Make sure you have followed the above mentioned steps :)__

## Table of contents.

* [Syntax](#syntax)
* [Doctype](#doctype)
* [Language attribute](#language)
* [Internet Explorer compatibility mode](#ie compatibility mode)
* [Character encoding](#character encoding)
* [CSS and JavaScript includes](#css and js includes)
* [Practicality over purity](#practicality over purity)
* [Attribute order](#attribute order)
* [Boolean attributes](#boolean attributes)
* [Reducing markup](#reducing markup)
* [JavaScript generated markup](#js generated markup)



## Syntax
- Use soft tabs with two spaces—they're the only way to guarantee code renders the same in any environment.
- Nested elements should be indented once (two spaces).
- Always use double quotes, never single quotes, on attributes.
- Don't include a trailing slash in self-closing elements—the HTML5 spec says they're optional.
- Don’t omit optional closing tags (e.g. `</li>` or `</body>`).

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Page title</title>
  </head>
  <body>
    <img src="images/company-logo.png" alt="Company">
    <h1 class="hello-world">Hello, world!</h1>
  </body>
</html>
```

## Doctype
- Enforce standards mode and more consistent rendering in every browser possible with this simple doctype at the beginning of every HTML page.

```html
<!DOCTYPE html>
<html>
  <head>
  </head>
</html>
```

## Language
- Developers are encouraged to specify a lang attribute on the root html element, giving the document's language. This aids speech synthesis tools to determine what pronunciations to use, translation tools to determine what rules to use, and so forth.
- Read more about the `lang` [attribute in the spec.](http://www.w3.org/html/wg/drafts/html/master/#the-html-element)
- Sitepoint [list of language codes.](http://www.sitepoint.com/web-foundations/iso-2-letter-language-codes/)

```html
<html lang="en-us">
  <!-- ... -->
</html>
```

## Internet Explorer compatibility mode ##
- Internet Explorer supports the use of a document compatibility `<meta>` tag to specify what version of IE the page should be rendered as. Unless circumstances require otherwise, it's most useful to instruct IE to use the latest supported mode with **edge mode.**
- For more information, read this awesome [Stack Overflow article](http://stackoverflow.com/questions/6771258/whats-the-difference-if-meta-http-equiv-x-ua-compatible-content-ie-edge-e).

```html
<meta http-equiv="X-UA-Compatible" content="IE=Edge">
```
- Using the `meta` tag mentioned above will through a validation error. To fix the validation error, simply paste the below code to your `.htaccess` file.

``` .htaccess
<IfModule mod_headers.c>
    Header set X-UA-Compatible "IE=edge"
    # `mod_headers` cannot match based on the content-type, however,
    # the `X-UA-Compatible` response header should be send only for
    # HTML documents and not for the other resources.
    <FilesMatch "\.(appcache|atom|bbaw|bmp|crx|css|cur|eot|f4[abpv]|flv|geojson|gif|htc|ico|jpe?g|js|json(ld)?|m4[av]|manifest|map|mp4|oex|og[agv]|opus|otf|pdf|png|rdf|rss|safariextz|svgz?|swf|topojson|tt[cf]|txt|vcard|vcf|vtt|webapp|web[mp]|woff2?|xloc|xml|xpi)$">
        Header unset X-UA-Compatible
    </FilesMatch>
</IfModule>
```

## Character Encoding
- Quickly and easily ensure proper rendering of your content by declaring an explicit character encoding. When doing so, you may avoid using character entities in your HTML, provided their encoding matches that of the document (generally UTF-8).

```html
<head>
  <meta charset="UTF-8">
</head>
```

## CSS and JavaScript includes
- As per the HTML5 spec, typically there is no need to specify a type when including CSS and JavaScript files as text/css and text/javascript are their respective defaults.

```html
<!-- External CSS -->
<link rel="stylesheet" href="code-guide.css">

<!-- In-document CSS -->
<style>
  /* ... */
</style>

<!-- JavaScript -->
<script src="code-guide.js"></script>
```

## Practicality over purity
- Strive to maintain HTML standards and semantics, but not at the expense of practicality. Use the least amount of markup with the fewest intricacies whenever possible.

## Attribute order
HTML attributes should come in this particular order for easier reading of code.

- `class`
- `id`, `name`
- `data-*`
- `src`, `for`, `type`, `href`, `value`
- `title`, `alt`
- `aria-*`, `role`

Classes make for great reusable components, so they come first. Ids are more specific and should be used sparingly (e.g., for in-page bookmarks), so they come second.

```html
<a class="..." id="..." data-modal="toggle" href="#">
  Example link
</a>

<input class="form-control" type="text">

<img src="..." alt="...">
```
## Boolean attributes
- A boolean attribute is one that needs no declared value. XHTML required you to declare a value, but HTML5 has no such requirement.

- The presence of a boolean attribute on an element represents the true value, and the absence of the attribute represents the false value.

- In short, don't add a value.

```html
<input type="text" disabled>

<input type="checkbox" value="1" checked>

<select>
  <option value="1" selected>1</option>
</select>
```

## Reducing markup
Whenever possible, avoid superfluous parent elements when writing HTML. Many times this requires iteration and refactoring, but produces less HTML. Take the following example:

```html
<!-- Not so great -->
<span class="avatar">
  <img src="...">
</span>

<!-- Better -->
<img class="avatar" src="...">
```

## JavaScript generated markup
Writing markup in a JavaScript file makes the content harder to find, harder to edit, and less performant. Avoid it whenever possible.
