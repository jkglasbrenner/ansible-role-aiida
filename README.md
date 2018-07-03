# Ansible Role: AiiDA

[![Build Status](https://travis-ci.org/jkglasbrenner/ansible-role-aiida.svg?branch=master)](https://travis-ci.org/jkglasbrenner/ansible-role-aiida)

Installs and configures [AiiDA](http://www.aiida.net) on Debian-based Linux distributions. AiiDA (Automated Interactive Infrastructure and Database for Computational Science) is a flexible and scalable informatics' infrastructure to manage, preserve, and disseminate the simulations, data, and workflows of modern-day computational science.

Install this role using `ansible-galaxy`:

```bash
ansible-galaxy install jkglasbrenner.aiida
```

## Requirements

*   [Anaconda](https://www.anaconda.com/distribution/)

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
aiida_conda_packages:
  - cython=0.28.3
  - gcc_linux-64=7.2.0
  - libffi=3.2.1
  - libpq=10.3
  - numpy=1.14.3
  - numpy-base=1.14.3
  - pandoc=2.2.1
  - python=2.7
  - scipy=1.1.0
  - spglib=1.9.10.1
  - qt=5.9.6
  - zeromq=4.2.5
aiida_pypi_packages:
  - "aiida=={{ aiida_version }}"
  - "aiida-core[atomic_tools,ssh_kerberos,rest,docs,advanced_plotting,notebook,testing]"
```

Distribution-specific variables:

```yaml
# Debian-based distributions
aiida_package_dependencies:
  - libpq-dev
  - postgresql
  - postgresql-server-dev-all
  - postgresql-client
  - python-psycopg2
```

## Dependencies

```yaml
dependencies:
  - role: jkglasbrenner.miniconda
  - role: geerlingguy.postgresql
    become: yes
    vars:
      postgresql_python_library: python-psycopg2
      postgresql_users:
        - name: aiida
          state: present
          port: 5432
```

## Example Playbook

```yaml
- hosts: all
  roles:
    - jkglasbrenner.aiida
```


## License

MIT
