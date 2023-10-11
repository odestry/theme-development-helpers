# Theme Development Helpers

[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat&colorA=338fbb&colorB=1c1c1c&logoColor=ffffff)](https://github.com/odestry/.github/blob/main/CONTRIBUTING.md)
[![CI](https://img.shields.io/github/actions/workflow/status/odestry/theme-development-helpers/ci.yml?style=flat&label=CI&colorA=338fbb&colorB=1c1c1c&logoColor=ffffff)](https://github.com/odestry/theme-development-helpers/blob/main/.github/workflows/ci.yml)
[![Discord Shield](https://img.shields.io/discord/983602196493004820?style=flat&colorA=338fbb&colorB=1c1c1c&label=discord&logo=discord&logoColor=ffffff)](https://discord.gg/blanklob-community-983602196493004820)

[Usage](#usage) |
[Contributing](#contributing) |
[License](#license)

A growing collection of useful helpers and fully functional, ready-made utils for Shopify theme development. If you make a snippet that is generic enough to be useful to others, think about [CONTRIBUTING](#contributing).

## Usage

Copy the code from the snippet you want to use and paste it into your theme's `/snippets` folder. Then include the snippet in your theme sections.

```liquid
{% render 'snippet-name' %}
```

You can also use our theme starter template to quickly preview these helpers. See [odestry/theme-starter](https://github.com/odestry/theme-starter).

### Theme app extensions

For theme app extensions, you can do the same thing as above, but instead of sections, you include the snippet in your app blocks.

### Index

You can navigate these snippets by using the table below.

| Category | Snippet | Description |
| --- | --- | --- |
| [Tools](#tools) | [Development screen indicator](#development-screen-indicator) | A simple indicator that shows which viewport size you are in. Useful for debugging and development.
| [Tools](#tools) | [Metaobject detector](#metaobject-detector) | A way to detect the current metaobject on the metaobject template without relying on dynamic ressources.
| [Meta](#meta) | [Social share](#social-share) | A small snippet to render all necessary meta tags for social sharing and page previews on socials. |
| [UI](#ui) | [Image](#image) | A powerful, less opinionated image snippet built on top of evergreen web technologies for Shopify storefronts. |
| [Schemas](#schemas) | [Schema website](#schema-website) | Renders the schema.org website JSON-LD for Site Name. |
| [Schemas](#schemas) | [Schema organization](#schema-organization) | Renders the schema.org JSON-LD for Brand and Organization. |
| [Schemas](#schemas) | [Schema article](#schema-article) | Renders the schema.org JSON-LD for a blog post or an article. |

## Tools

These are tools that can be used to enhance the theme development experience.

### Development screen indicator

A simple indicator that shows which viewport size you are in. Useful for debugging and development.

Built with [Tailwind CSS](https://tailwindcss.com) and can be added on the `theme.liquid` layout file.

Copy code from [this file](./tools/development-screen-indicator.liquid).

```liquid
{% liquid
  if settings.enable_development_mode
    render 'development-screen-indicator'
  endif
%}
```

An example of a setting to enable the development screen indicator on demand:

```json
{
  "type": "checkbox",
  "id": "enable_development_mode",
  "label": "Enable development mode",
  "default": false
}
```

### Metaobject detector

This must be used inside a metaobject template. It detects the current metaobject and renders its properties or other metaobjects if it has any.

Copy code from [this file](./tools/metaobject-detector.liquid).

```liquid
{% render 'metaobject-detector' %}
```

Learn more about metaobject templates [here](https://shopify.dev/docs/themes/architecture/templates/metaobject).

## Meta

These are snippets that render meta tags to enhance the storefront with additional information.

### Social share

A small snippet to render all necessary meta tags for social sharing and page previews on socials.

Copy code from [this file](./meta/social-share.liquid).

```liquid
{% render 'social-share' %}
```

You can also check Shopify [recommandations](https://help.shopify.com/manual/online-store/images/showing-social-media-thumbnail-images) on social sharing.

#### Debugging previews

To debug your social share previews, you can use the [Facebook Sharing Debugger](https://developers.facebook.com/tools/debug/) and the [Twitter Card Validator](https://cards-dev.twitter.com/validator).

## Schemas

These JSON-LD snippets are based on the [Schema.org](https://schema.org) vocabulary and are used to improve the display of your pages on search engines.

### Schema website

Renders the schema.org website JSON-LD for Site Names.

Copy code from [this file](./schemas/schema-website.liquid).

```liquid
{% render 'schema-website' %}
```

> You can check the [Google Structured Data Docs](https://developers.google.com/search/docs/appearance/site-names) for more information.

### Schema organization

Renders the schema.org JSON-LD for Brand and Organization. Must be used on all templates.

Copy code from [this file](./schemas/schema-organization.liquid).

```liquid
{% render 'schema-organization' %}
```

> You can check the [Google Structured Data Docs](https://developers.google.com/search/docs/appearance/structured-data/logo) for more information about this schema.

### Schema article

Renders the schema.org JSON-LD for Blog post and article. Must be used on article cards or templates.

Copy code from [this file](./schemas/schema-article.liquid).

```liquid
{% render 'schema-article' article: block.settings.article %}
```

> You can check the [Google Structured Data Docs](https://developers.google.com/search/docs/appearance/structured-data/article) for more information about this schema.

#### Debugging structured data

To debug your structured data, you can use the [Google Structured Data Testing Tool](https://search.google.com/structured-data/testing-tool) and the [Google Rich Results Test](https://search.google.com/test/rich-results).

## UI

These are user interface snippets that are optimized and can be reused within your theme.

### Image

A powerful, less opinionated image snippet built on top of evergreen web technologies for Shopify storefronts.

Copy code from [this file](./ui/image.liquid).

Check more informations about this image snippet as well as a preview of the snippet in action [here](https://github.com/odestry/theme-image).

#### Arguments

The image has a very easy-to-understand sample API, and all of these arguments are optional:

- `image`: The image object. This can be a product image or a media object of type image as well.
- `class`: A string of classes, same as the class HTML attribute.
- `lazyload`: By default, the snippet is eagerly loaded. If you want to lazyload the image, you can set this boolean parameter to true.
- `width`: This is the maximum width of the srcset. In some cases, it makes sense to load a smaller srcset if the image is small.
- `alt`: You can set a custom alt text. By default, Shopify uses the product title as the alt text if the image is associated with a product.
- `placeholder`: The placeholder handle that is defined by Shopify. If you want to set other types of placeholders, check the Shopify documentation.

#### Examples

There are many different ways to use this snippet. The easiest one is just by calling it with a render tag.

##### Displaying a placeholder

If the image is blank or doesn't have any image object, it displays a placeholder like the following:

```liquid
{% render 'image' %}
```

You can also pass a placeholder names handle to the snippet:

```liquid
{% render 'image', placeholder: 'product-apparel-4' %}
```

> You can check a list of all the available placeholders illustrations [here](https://shopify.dev/docs/api/liquid/filters#placeholder_svg_tag).

##### Displaying product featured image

You can easily display a product image with the following:

```liquid
{% render 'image' with product.featured_image %}
```

Which is the same as:

```liquid
{% render 'image', image: product.featured_image %}
```

It also accepts multiple arguments at once:

```liquid
{% render 'image' with product.featured_image,
  alt: product.title,
  class: 'aspect-square object-center',
  lazyload: true,
  placeholder: 'hero-apparel-3'
%}
```

##### Lazyload images in a product grid

You can lazyload images if the grid is made of different product cards, for example, and set the lazyload attribute based on the current position of the image on the grid.

```liquid
{% liquid
  assign lazyload = false
  for product in collection.products
    if forloop.index > 6
      assign lazyload = true
    endif

    render 'image' with product.featured_image, lazyload: lazyload
  endfor
%}
```

##### Set aspect ratio of the image

We recommend using the native browser aspect ratio CSS rule. An example would be to create a class for each of these rules and pass it via the class argument like the following:

```liquid
{% render 'image' with product.featured_image, class: 'aspect-square' %}
```

**If you don't use tailwind, you can set this class on the image instead:**

```css
.image {
  display: block;
  vertical-align: middle;
  aspect-ratio: auto;
  height: auto;
  object-fit: cover;
  max-width: 100%;
}
```

And then set this on the snippet class default value:

```liquid
  ...
  assign class = 'image ' | append: class
  ...
```

## Contributing

We'd love your help! Please read our [contributing guide](https://github.com/odestry/.github/blob/main/CONTRIBUTING.md) to learn about our development process, how to propose bug fixes and improvements.

## License

Copyright (c) 2023-present Odestry. See [LICENSE](/LICENSE.md) for further details.
