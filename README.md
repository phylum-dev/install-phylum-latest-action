# install-phylum-latest-action
A GitHub Action to install the latest version of the Phylum [command-line tool](https://github.com/phylum-dev/cli).

This action enables users to download, install, and configure the Phylum command-line interface (CLI) tool for use. The Phylum CLI tool allows users to submit their project package dependencies to Phylum's API for analysis. 

Phylum provides a complete risk analyis of "open-source packages" (read: untrusted software from random Internet strangers). Phylum evolved forward from legacy SCA tools to defend from supply-chain malware, malicious open-source authors, and engineering risk, in addtion to software vulnerabilities and license risks. To learn more, please see [our website](https://phylum.io).



## Features
- can be used by other GitHub Actions to set Phylum up in the environment

## Getting Started
This is a sample workflow using this action. Note the `export` to add the phylum install directory to your `PATH`.
```yaml
on: [push]

jobs:
  test_install_phylum_job:
    runs-on: ubuntu-latest
    name: A job to test phylum
    steps:
      - uses: actions/checkout@v2
      - id: phylum-test
        uses: phylum-dev/install-phylum-latest-action@master
        with:
          phylum_token: ${{ secrets.PHYLUM_TOKEN }}

      - name: Run phylum to test auth with token
        shell: bash
        run: |
          export PATH="$HOME/.phylum:$PATH"
          phylum projects
```


### Requirements:
- active Phylum account ([Register here](https://app.phylum.io/auth/registration))
- mandatory inputs:
  
  `phylum_token` - the API authentication token for your account
