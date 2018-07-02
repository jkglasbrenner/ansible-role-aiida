# Ansible Role: AiiDA

[![Build Status](https://travis-ci.org/jkglasbrenner/ansible-role-aiida.svg?branch=master)](https://travis-ci.org/jkglasbrenner/ansible-role-aiida)

Installs and configures [AiiDA](http://www.aiida.net) on Debian-based Linux distributions. AiiDA (Automated Interactive Infrastructure and Database for Computational Science) is a flexible and scalable informatics' infrastructure to manage, preserve, and disseminate the simulations, data, and workflows of modern-day computational science.

Install this role using `ansible-galaxy`:

```bash
ansible-galaxy install jkglasbrenner.aiida
```

## Requirements

*   `python` (2.7.x): installed using [Anaconda](https://www.anaconda.com/distribution/)

*   `pip`: installed automatically with [Anaconda](https://www.anaconda.com/distribution/)

*   `postgresql` (>=9.4)

## Role Variables

Variables and default values:

```yaml
# aiida install info
aiida_version: 0.12.1

# virtual environment configuration
aiida_env_name: aiidapy
aiida_env_channels:
  - defaults
  - conda-forge
aiida_env_dependencies:
  - amqp=1.4.9
  - anyjson=0.3.3
  - billiard=3.3.0.23
  - click-plugins=1.0.3
  - click=6.7
  - codecov=2.0.9
  - coverage=4.5.1
  - docutils=0.13.1
  - ecdsa=0.13
  - enum34=1.1.6
  - flask-cache=0.13.1
  - flask-httpauth=3.2.0
  - flask-marshmallow=0.7.0
  - flask=0.10.1
  - future=0.16.0
  - ipython=5.7.0
  - itsdangerous=0.24
  - jinja2=2.9.5
  - jupyter=1.0.0
  - markupsafe=0.23
  - mock=2.0.0
  - numpy=1.14.3
  - paramiko=2.4.0
  - passlib=1.7.1
  - pathlib2=2.3.0
  - pattern=2.6
  - portalocker=1.1.0
  - psutil=5.4.0
  - pyasn1=0.3.7
  - pycrypto=2.6.1
  - pygments=2.2.0
  - pylint=1.8.4
  - pymysql=0.7.9
  - pyparsing=2.1.10
  - python-dateutil=2.6.0
  - python-memcached=1.58
  - python=2.7
  - pyyaml=3.12
  - singledispatch=3.4.0.3
  - six=1.11.0
  - spglib=1.9.10.1
  - tabulate=0.7.5
  - toml=0.9.4
  - ujson=1.35
  - validate_email=1.3
  - voluptuous=0.8.11
```

Distribution-specific variables:

```yaml
# Debian-based distributions
aiida_package_dependencies:
  - build-essential
  - git
  - python2.7-dev
  - python-pip
  - virtualenv
  - postgresql
  - postgresql-server-dev-all
  - postgresql-client
```

## Dependencies

```yaml
dependencies:
  - jkglasbrenner.miniconda
```

## Example Playbook

```yaml
- hosts: all
  roles:
    - role: jkglasbrenner.aiida
```


## License

MIT
