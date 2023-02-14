[![Open-CE-Python Stars](https://img.shields.io/github/stars/open-ce-python?style=social)](https://github.com/open-ce/open-ce-python/stargazers)

<p align="center">
  <img src="https://avatars0.githubusercontent.com/u/68873540?s=400&u=a02dc4156e50cdffb23172aba7133e44381885d4&v=4" alt="Open-CE Logo" width="30%">
</p>

[![Python Support](https://img.shields.io/badge/python-3.10-blue.svg)](#requirements)
[![Architecture Support](https://img.shields.io/badge/architecture-ppc64le-blue)](#)
[![GitHub Licence](https://img.shields.io/github/license/open-ce/open-ce.svg)](LICENSE)
---

This is a sub-project of the Open-CE project for building python specifically optimized for Power10 architecture.

This repository contains an Open-CE environment file that builds optimized python using the [python feedstock](https:///github.com/open-ce/python-feedstock). Open-CE Python currently supports the following:

| | Supported Versions |
| --- | --- |
| Architecture | Power |
| Python | 3.10 |

## GETTING STARTED

### Requirements

* `conda`
  * The conda tool can either be installed through [Anaconda](https://www.anaconda.com/products/individual#Downloads) or [Miniconda](https://docs.conda.io/en/latest/miniconda.html).

* `Redhat GCC 11`
  Redhat's `gcc-toolset-11` package is needed which can be installed via `yum install -y gcc-toolset-11`. 
  
* `System/OS`
  RHEL 8.x with Power 9 or Power 10 architecture is required.

### Building Open-CE Python

Open-CE Python can be built like any other Open-CE package. This repository contains [envs/python-env.yaml](https://github.com/open-ce/open-ce-python/blob/main/envs/python-env.yaml) which is to be used to build optimized python. The `open-ce` tool can be used to build this python. For more information on the `open-ce` tool, please see the Open-CE Builder [repository](https://github.com/open-ce/open-ce-builder/blob/main/doc/README.open_ce_build.md).

For example:
```shell
    open-ce build env --python_versions=3.10 --ppc_arch=p10 --output_folder=condabuild --build_type=cpu python-env.yaml
```

### Using Open-CE python with other Open-CE packages

One can use Open-CE packages along with the optimized Open-CE Python. Following are the steps to setup Open-CE Python and Open-CE packages in a single conda environment -

1. Create a new conda environment with optimized python built as mentioned in above section.
```shell
    conda create -n <conda env name> python=3.10.9 -c file://<path to condabuild directory>
```
   Here, `path to condabuild directory` means the path to `--output_folder` when python was built as per above section.
   If you have not specified `--output-folder` during the build, the directory will be `condabuild`.

2. Activate the conda environment
```shell
    conda activate <conda env name>
```

3. Confirm the source of python package in the environment
```shell
    (<conda env name>)$ conda list python
    # packages in environment at $HOME/anaconda3/envs/<conda env name>:
    #
    # Name                    Version                   Build  Channel
    python                    3.10.9               hd70dfa7_0    file://<path to condabuild directory>
```

4. Install Open-CE packages from any of the following channels -
5. 
   * https://anaconda.org/rocketce/
   * https://ftp.osuosl.org/pub/open-ce/current/
   * https://opence.mit.edu/

For example:
```shell
    conda install -y tensorflow-cpu libtensorflow onnx onnxruntime pytorch-cpu openblas -c rocketce
```

5. Python Verification
   When you're done with the package installation, run `(<conda env name>)$ conda list python` again to ensure that the python installed in the conda environment is not updated/replaced by any other python source like Anaconda.

## Contributions

For contribution information, please see the [CONTRIBUTING.md](https://github.com/open-ce/open-ce/blob/main/CONTRIBUTING.md) page.

## Slack Community

Join us on [Slack!](http://open-ce.slack.com/) Use [this link](https://join.slack.com/t/open-ce/shared_invite/zt-o27t9db6-oUklancQvdGO8FIwftDwgw) or ping the [@open-ce/open-ce-dev-team](https://github.com/orgs/open-ce/teams/open-ce-dev-team) for an invite.

