# Theme Development Helpers

[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat&colorA=338fbb&colorB=1c1c1c&logoColor=ffffff)](/.github/CONTRIBUTING.md)
[![Discord Shield](https://img.shields.io/discord/983602196493004820?style=flat&colorA=338fbb&colorB=1c1c1c&label=discord&logo=discord&logoColor=ffffff)](https://discord.gg/blanklob-community-983602196493004820)

[Contributing](#contributing) |
[License](#license)

A growing collection of useful helpers and fully functional, ready-made utils for Liquid theme development. If you make a snippet that is generic enough to be useful to others, think about [CONTRIBUTING](./CONTRIBUTING.md).

## Tools

### Development screen indicator

A simple indicator that shows if you are on a development screen. Useful for debugging and development.

Built with [Tailwind CSS](https://tailwindcss.com/) and can be added on the `theme.liquid` layout file.

```liquid
{% liquid 
    if settings.enable_development_mode
        render 'development-screen-indicator' 
    endif
%}
```

An example setting to enable the development screen indicator:

```json
{
    "type": "checkbox",
    "id": "enable_development_mode",
    "label": "Enable development mode",
    "default": false
}
```

## Contributing

We'd love your help! Please read our [contributing guide](./CONTRIBUTING.md) to learn about our development process, how to propose bug fixes and improvements.

## License

Copyright (c) 2023-present Odestry. See [LICENSE](/LICENSE.md) for further details.
