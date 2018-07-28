# Ansible Role: AiiDA

[![Build Status](https://travis-ci.org/jkglasbrenner/ansible-role-aiida.svg?branch=master)](https://travis-ci.org/jkglasbrenner/ansible-role-aiida)

Installs and configures [AiiDA](http://www.aiida.net) on Debian-based Linux distributions. AiiDA (Automated Interactive Infrastructure and Database for Computational Science) is a flexible and scalable informatics' infrastructure to manage, preserve, and disseminate the simulations, data, and workflows of modern-day computational science.

Install this role using `ansible-galaxy`:

```bash
ansible-galaxy install jkglasbrenner.aiida
```

## Requirements

*   [Anaconda](https://www.anaconda.com/distribution/) (>=5.2), use the [`jkglasbrenner.miniconda` role](https://galaxy.ansible.com/jkglasbrenner/miniconda) if not available
    
    ```bash
    ansible-galaxy install jkglasbrenner.miniconda
    ```

*   `postgresql` (>=9.4), use the [`geerlingguy.postgresql` role](https://galaxy.ansible.com/geerlingguy/postgresql) if not available
    
    ```bash
    ansible-galaxy install geerlingguy.postgresql
    ```

## Role Variables

Variables and default values:

```yaml
# plugin urls
aiida_quantum_espresso_url: "https://github.com/aiidateam/aiida-quantumespresso.git"

# aiida install info
aiida_version: 1.0.0a2
aiida_quantum_espresso_version: 3.0.0a1

# virtual environment configuration
aiida_user: "{{ lookup('env', 'USER') | default('root', true) }}"
aiida_env_name: aiidapy
aiida_env_channels:
  - defaults
  - conda-forge
aiida_conda_packages_list:
  0.12.1:
    - cython=0.28.4
    - gcc_linux-64=7.2.0
    - krb5=1.16.1
    - libffi=3.2.1
    - numpy=1.14.3
    - numpy-base=1.14.3
    - pandoc=2.2.1
    - python=2.7
    - scipy=1.1.0
    - spglib=1.9.10.1
    - qt=5.9.6
    - zeromq=4.2.5
  1.0.0a2:
    - cython=0.28.4
    - gcc_linux-64=7.2.0
    - krb5=1.16.1
    - libffi=3.2.1
    - numpy=1.14.3
    - numpy-base=1.14.3
    - pandoc=2.2.1
    - python=2.7.15
    - qt=5.9.6
    - scipy=1.1.0
    - spglib=1.10.3.65
    - zeromq=4.2.5
aiida_pypi_packages_list:
  0.12.1:
    - "aiida=={{ aiida_version }}"
    - "aiida-core[atomic_tools,ssh_kerberos,rest,docs,advanced_plotting,notebook,testing]"
  1.0.0a2:
    - "aiida-core=={{ aiida_version }}"
    - "aiida-core[atomic_tools,ssh_kerberos,rest,docs,advanced_plotting,notebook,testing]"
    - "aiida-ase"
    - "aiida-codtools"
    - "aiida-nwchem"
    - "git+{{ aiida_quantum_espresso_url }}@v{{ aiida_quantum_espresso_version }}"
aiida_conda_packages: "{{ aiida_conda_packages_list[aiida_version] }}"
aiida_pypi_packages: "{{ aiida_pypi_packages_list[aiida_version] }}"
```

Distribution-specific variables:

```yaml
# Debian-based distributions
aiida_package_dependencies_list:
  0.12.1:
    - libpq-dev
    - postgresql
    - postgresql-server-dev-all
    - postgresql-client
    - python-psycopg2
  1.0.0a2:
    - libpq-dev
    - postgresql
    - postgresql-server-dev-all
    - postgresql-client
    - python-psycopg2
    - rabbitmq-server
aiida_package_dependencies: "{{ aiida_package_dependencies_list[aiida_version] }}"
```

## Dependencies

None.

## Example Playbook

```yaml
- hosts: all
  become: yes
  roles:
    - role: jkglasbrenner.miniconda
    - role: geerlingguy.postgresql
    - role: jkglasbrenner.aiida
  vars:
    aiida_user: jkglasbrenner
    miniconda_dir: "/opt/miniconda"
    postgresql_python_library: python-psycopg2
```

## License

MIT
