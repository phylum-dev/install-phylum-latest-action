# install-phylum-latest-action
A GitHub Action to install the latest version of the Phylum [command-line tool](https://github.com/phylum-dev/cli).

This action enables users to download, install, and configure the Phylum command-line interface (CLI) tool for use.
The Phylum CLI tool allows users to submit their project package dependencies to Phylum's API for analysis.

Phylum provides a complete risk analyis of "open-source packages" (read: untrusted software from random Internet
strangers). Phylum evolved forward from legacy SCA tools to defend from supply-chain malware, malicious open-source
authors, and engineering risk, in addition to software vulnerabilities and license risks. To learn more, please see
[our website](https://phylum.io).

## Features
- can be used by other GitHub Actions to set Phylum up in the environment

## Getting Started
This is a sample workflow using this action.

```yaml
on: [push]

jobs:
  test_install_phylum_job:
    runs-on: ubuntu-latest
    name: A job to test phylum
    steps:
      - uses: actions/checkout@v2
      - id: phylum-test
        uses: phylum-dev/install-phylum-latest-action@v1
        with:
          phylum_token: ${{ secrets.PHYLUM_TOKEN }}

      - name: Run phylum to test auth with token
        shell: bash
        run: |
          phylum project
```

### Requirements
- active Phylum account ([Register here](https://app.phylum.io/auth/registration))
- a Linux runner (e.g., `runs-on: ubuntu-*` for the GitHub hosted runners)
  - technically, the runner just needs to match the `x86_64-unknown-linux-musl` Rust target
- mandatory inputs:
  - `phylum_token` - the API authentication token for your account
- optional inputs:
  - `phylum_version` - a specific version of the Phylum CLI to install
    - NOTE: when not specified, the `latest` version will be installed
    - NOTE: the Phylum CLI 2.0.0 release changed the way the artifacts are packaged and released, which means this
            option should **NOT specify a version less than 2.0.0**

### License

Copyright (C) 2022  Phylum, Inc.

This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public
License as published by the Free Software Foundation, either version 3 of the License or any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied
warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this program.
If not, see <https://www.gnu.org/licenses/gpl.html> or write to `phylum@phylum.io` or `engineering@phylum.io`
