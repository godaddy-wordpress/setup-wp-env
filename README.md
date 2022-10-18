# Setup @wordpress/env (wp-env)

This Action will setup and start [@wordpress/env](https://github.com/WordPress/gutenberg/tree/HEAD/packages/env) for quick and efficient continuous integration (CI) testing with WordPress.

## Usage

Use this Action in one of your project [workflows](https://docs.github.com/en/actions/using-workflows) steps:

```yaml
jobs:
  wp-env:
    runs-on: ubuntu-latest
    name: Setup WordPress environment
    steps:
      - name: Start wp-env
        uses: godaddy-wordpress/setup-wp-env@v1
```

### Usage with wp-env.json

This Action assumes that no `wp-env.json` is present in the project that uses this Action in a workflow. If a `wp-env.json` file is present in the project, this Action config will override that config; however, if no inputs are provided that already exist in `wp-env.json`, those will be used instead (this is how `@wordpress/env` is designed).

If your project includes a `wp-env.json` at root, it is best to explicitly add all necessary inputs in order to override the `wp-env.json` which exists in the project.

## Options

This action allows configuration of each option found in [`wp-env.json`](https://github.com/WordPress/gutenberg/tree/HEAD/packages/env#wp-envjson), except the port (it is unnecessary, as each runner is encapsulated). These are added as strings, and later converted to JSON and added to `wp-env.override.json`.

### Examples

```yaml
- name: Start wp-env
  uses: godaddy-wordpress/setup-wp-env@v1
  with:
    core: "WordPress/WordPress#5.9"
    phpVersion: "7.4"
    plugins: ["https://downloads.wordpress.org/plugin/coblocks.zip"]
    themes: ["https://downloads.wordpress.org/theme/go.zip"]
```

> Please note that when adding plugins and themes for integration testing, it is a best practice to use the official released of those projects (not development versions). This will greatly reduce the time for setup and ensures you are only downloading the necessary code for testing.

---

## License

This project is licensed under the GPL. Use it to make something cool, have fun, and share what you've learned with others.

This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 2 of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

---

Copyright © 2022 GoDaddy Operating Company, LLC. All Rights Reserved.

[godaddy.com](https://www.godaddy.com) &nbsp;&middot;&nbsp;
GitHub [@godaddy-wordpress](https://github.com/godaddy-wordpress) &nbsp;&middot;&nbsp;
Twitter [@GoDaddyOSS](https://twitter.com/GoDaddyOSS)
