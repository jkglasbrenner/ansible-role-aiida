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
  - cython=0.28.3
  - docutils=0.13.1
  - ecdsa=0.13
  - enum34=1.1.6
  - flask-cache=0.13.1
  - flask-httpauth=3.2.0
  - flask-marshmallow=0.7.0
  - flask=0.10.1
  - future=0.16.0
  - imagesize=1.0.0
  - ipython=5.7.0
  - itsdangerous=0.24
  - jinja2=2.9.5
  - jupyter=1.0.0
  - mako=1.0.7
  - markupsafe=0.23
  - mock=2.0.0
  - numpy=1.14.3
  - numpy-base=1.14.3
  - packaging=17.1
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
  - scipy=1.1.0
  - singledispatch=3.4.0.3
  - six=1.11.0
  - snowballstemmer=1.2.1
  - spglib=1.9.10.1
  - subprocess32=3.5.2
  - tabulate=0.7.5
  - toml=0.9.4
  - typing=3.6.4
  - ujson=1.35
  - validate_email=1.3
  - voluptuous=0.8.11
aiida_pypi_packages:
  - aiida==0.12.1
  - aiida-ase==1.0.1
  - aiida-codtools==1.0.1
  - aiida-core==0.12.1
  - aiida-nwchem==1.0.2
  - aiida-quantumespresso==2.1.0
  - alabaster==0.7.11
  - aldjemy==0.6.0
  - alembic==0.9.6
  - aniso8601==3.0.2
  - ase==3.12.0
  - babel==2.6.0
  - celery==3.1.25
  - chainmap==1.0.2
  - click-spinner==0.1.8
  - cycler==0.10.0
  - django==1.7.11
  - django-extensions==1.5.0
  - ete3==3.0.0b35
  - flask-cors==3.0.1
  - flask-restful==0.3.6
  - flask-sqlalchemy==2.1
  - frozendict==1.2
  - kiwisolver==1.0.1
  - kombu==3.0.37
  - marshmallow-sqlalchemy==0.10.0
  - matplotlib==2.2.2
  - meld3==1.0.0
  - monty==1.0.3
  - palettable==3.1.1
  - pg8000==1.12.2
  - pgtest==1.1.0
  - plumpy==0.7.12
  - psycopg2-binary==2.7.4
  - py==1.5.4
  - pycifrw==4.2.1
  - pydispatcher==2.0.5
  - pymatgen==4.5.3
  - python-editor==1.0.3
  - python-gssapi==0.6.4
  - python-mimeparse==0.1.4
  - pytz==2014.10
  - qe-tools==1.1.0
  - reentry==1.2.0
  - seekpath==1.8.0
  - sphinx==1.7.2
  - sphinx-rtd-theme==0.2.5b2
  - sphinxcontrib-websupport==1.1.0
  - sqlalchemy==1.0.19
  - sqlalchemy-diff==0.1.3
  - sqlalchemy-migrate==0.11.0
  - sqlalchemy-utils==0.33.0
  - sqlparse==0.2.4
  - tempita==0.5.2
  - tzlocal==1.3
  - uritools==1.0.2
```

Distribution-specific variables:

```yaml
# Debian-based distributions
aiida_package_dependencies:
  - build-essential
  - libffi-dev
  - libkrb5-dev
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
    - jkglasbrenner.aiida
```


## License

MIT
