# Setup @wordpress/env (wp-env)

This Action will setup and start [@wordpress/env](https://github.com/WordPress/gutenberg/tree/HEAD/packages/env) for quick and efficient continuous integration (CI) testing with WordPress.

## Usage

Use this Action in one of your project [workflows](https://docs.github.com/en/actions/using-workflows) steps:

```yaml
jobs:
  wp-env:
    runs-on: ubuntu-latest
    name: Setup WordPress Environment
    steps:
      - name: Start wp-env
        uses: godaddy-wordpress/setup-wp-env@v1
```

### Usage with wp-env.json

This Action assumes that no `.wp-env.json` is present in the project that uses this Action in a workflow. If a `.wp-env.json` file is present in the project, this Action config will override that config; however, if no inputs are provided that already exist in `.wp-env.json`, those will be used instead (this is how `@wordpress/env` is designed).

If your project includes a `.wp-env.json` at root, it is best to explicitly add all necessary inputs in order to override the `.wp-env.json` which exists in the project.

## Options

This action allows configuration of each option found in [`wp-env.json`](https://github.com/WordPress/gutenberg/tree/HEAD/packages/env#wp-envjson), except the port (it is unnecessary, as each runner is encapsulated). These are added as strings, and later converted to JSON and added to `wp-env.override.json`.

### Examples

```yaml
- name: Start wp-env
  uses: godaddy-wordpress/setup-wp-env@v1
  with:
    core: 'WordPress/WordPress#5.9'
    phpVersion: '7.4'
    plugins: '["https://downloads.wordpress.org/plugin/coblocks.zip"]'
    themes: '["https://downloads.wordpress.org/theme/go.zip"]'
```

> Please note that when adding plugins and themes for integration testing, it is a best practice to use the official released of those projects (not development versions). This will greatly reduce the time for setup and ensures you are only downloading the necessary code for testing.

---

Copyright © 2022  [GoDaddy Operating Company, LLC](https://godaddy.com) &nbsp;&middot;&nbsp; All Rights Reserved &nbsp;&middot;&nbsp; [License](LICENSE)

[![GoDaddy Engineering](https://raw.githubusercontent.com/godaddy-wordpress/.github/master/assets/godaddy-oss-readme-banner.webp)](https://www.godaddy.com/engineering/)
