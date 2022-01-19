# install-phylum-latest-action
A GitHub Action to install the latest version of the Phylum command-line tool.

This action enables users to download, install, and configure the Phylum command-line interface (CLI) tool for use. The Phylum CLI tool allows users to submit their project package dependencies to Phylum's API for analysis. 

Phylum provides a complete risk analyis of "open-source packages" (read: untrusted software from random Internet strangers). Phylum evolved forward from legacy SCA tools to defend from supply-chain malware, malicious open-source authors, and engineering risk, in addtion to software vulnerabilities and license risks. To learn more, please see [our website](https://phylum.io).



## Features
- can be used by other GitHub Actions to set Phylum up in the environment

## Getting Started
```yaml
runs:
  using: "composite"
  steps:
    - id: phylum-install
      uses: phylum-dev/install-phylum-latest-action@master
      with:
        phylum_token: ${{ secrets.PHYLUM_TOKEN }}
```


### Requirements:
- active Phylum account ([Register here](https://app.phylum.io/auth/registration))
- mandatory inputs:
  
  `phylum_token` - the API authentication token for your account
