[![Open-CE-Python Stars](https://img.shields.io/github/stars/open-ce-python?style=social)](https://github.com/open-ce/open-ce-python/stargazers)

<p align="center">
  <img src="https://avatars0.githubusercontent.com/u/68873540?s=400&u=a02dc4156e50cdffb23172aba7133e44381885d4&v=4" alt="Open-CE Logo" width="30%">
</p>

[![Python Support](https://img.shields.io/badge/python-3.10-blue.svg)](#requirements)
[![Architecture Support](https://img.shields.io/badge/architecture-ppc64le-blue)](#)
[![GitHub Licence](https://img.shields.io/github/license/open-ce/open-ce.svg)](LICENSE)
---

This is a sub-project of the Open-CE project for building python optimized for Power10 architecture.

This repository contains an Open-CE environment file that builds optimized python using the [python feedstock](https:///github.com/open-ce/python-feedstock). Open-CE-Python currently supports the following:

| | Supported Versions |
| --- | --- |
| Architecture | Power |
| Python | 3.10 |

## GETTING STARTED

### Requirements

* `conda`
  * The conda tool can either be installed through [Anaconda](https://www.anaconda.com/products/individual#Downloads) or [Miniconda](https://docs.conda.io/en/latest/miniconda.html).

* `Redhat GCC 11`
  Redhat's `gcc-toolset-11` package is needed which can be installed via `yum install -y gcc-toolset-11`. RHEL 8.x with Power 9 or Power 10 architecture is required.

### Building Open-CE Python

Open-CE Python can be built like any other Open-CE package. This repository contains `envs/python-env.yaml` which is to be used to build optimized python. The `open-ce` tool can be used to build this python. For more information on the `open-ce` tool, please see the open-ce-builder [repository](https://github.com/open-ce/open-ce-builder).

For example:
```shell
    open-ce build env --python_versions=3.10 --ppc_arch=p10 --build_type=cpu python-env.yaml
```

## Contributions

For contribution information, please see the [CONTRIBUTING.md](CONTRIBUTING.md) page.

## Slack Community

Join us on [Slack!](http://open-ce.slack.com/) Use [this link](https://join.slack.com/t/open-ce/shared_invite/zt-o27t9db6-oUklancQvdGO8FIwftDwgw) or ping the [@open-ce/open-ce-dev-team](https://github.com/orgs/open-ce/teams/open-ce-dev-team) for an invite.

