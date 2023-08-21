# Theme Development Helpers

[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat&colorA=338fbb&colorB=1c1c1c&logoColor=ffffff)](./CONTRIBUTING.md)
[![Discord Shield](https://img.shields.io/discord/983602196493004820?style=flat&colorA=338fbb&colorB=1c1c1c&label=discord&logo=discord&logoColor=ffffff)](https://discord.gg/blanklob-community-983602196493004820)

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
| [Metas](#metas) | [Social share](#social-share) | A small snippet to render all necessary meta tags for social sharing and page previews on socials. |

## Tools

### Development screen indicator

A simple indicator that shows which viewport size you are in. Useful for debugging and development.

Built with [Tailwind CSS](https://tailwindcss.com/) and can be added on the `theme.liquid` layout file.

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

## Metas

### Social share

A small snippet to render all necessary meta tags for social sharing and page previews on socials.

```liquid
{% render 'social-share' %}
```

You can also check Shopify [recommandations](https://help.shopify.com/manual/online-store/images/showing-social-media-thumbnail-images) on social sharing.

#### Debugging previews

To debug your social share previews, you can use the [Facebook Sharing Debugger](https://developers.facebook.com/tools/debug/) and the [Twitter Card Validator](https://cards-dev.twitter.com/validator).

## Contributing

We'd love your help! Please read our [contributing guide](./CONTRIBUTING.md) to learn about our development process, how to propose bug fixes and improvements.

## License

Copyright (c) 2023-present Odestry. See [LICENSE](/LICENSE.md) for further details.
