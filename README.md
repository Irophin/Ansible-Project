<section align="center">
  <h1>
    Ansible Project
  </h1>

  <a href="./LICENSE">  
    <img src="https://img.shields.io/badge/License-MIT-yellow.svg" alt="License: MIT">
  </a>

  </br>

  <p>
    This project is an <strong>Ansible</strong> deployment aimed at setting up a web server.
    </br>
    It leverages the IUT <strong>OpenStack</strong> infrastructure to host a <strong>WordPress</strong> application connected to a database.
  </p>

  <div>
    <a href="https://www.ansible.com/">
      <img src="https://img.shields.io/badge/Ansible-grey" alt="Ansible">
    </a>
    <a href="https://iutdoua-os.univ-lyon1.fr/">
      <img src="https://img.shields.io/badge/OpenStack-red.svg" alt="OpenStack">
    </a>
    <a href="https://www.php.net/">
      <img src="https://img.shields.io/badge/PHP-blue.svg" alt="PHP">
    </a>
    <a href="https://www.mariaDB.org/">
      <img src="https://img.shields.io/badge/mariaDB-orange.svg" alt="MariaDB">
    </a>
    <a href="https://www.nginx.com/">
      <img src="https://img.shields.io/badge/Nginx-green.svg" alt="Nginx">
    </a>
  </div>

</section>

## Installation

This project requires **Ansible** to be installed on the host machine.<br>
If you haven't installed Ansible yet, you can do so by running the following command or referring to the [official documentation](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html):

```bash
pip3 install ansible
```

Remote hosts are expected to be running a **Debian**-based system.<br>
Ensure that you have SSH access to the remote hosts.<br>
All target hosts should be specified in the `inventories/hosts.yml` file. Specific variables can be set in the `host_vars` directory.

To decrypt the vault files, add a file named `.vault_pass.txt` to the root of the project containing the password. The committed vault files are encrypted using the password `#ZO0fi$7B!n6`.

To install the required dependencies, run the following command:

```bash
ansible-galaxy install -r requirements.yml
```

## Usage

To deploy the project, run the following command:

```bash
# Deploy the entire project
ansible-playbook deployment.yml

# Specific tags can be used to deploy only a part of the project
ansible-playbook deployment.yml --tags
  ├── dependencies # Install and update dependencies
  ├── webapp       # Deploy the web server
  ├── database     # Deploy the database
  │   └── db_init  # Initialize the database [Update root password, create new database, create new user]
  └── cleanup      # Destroy database and webapp folder

```

## Authors

- [Albert **VAILLON**](mailto:albert.vaillon@etu.univ-lyon1.fr) [p2106202]
- [Lilian **BAUDRY**](mailto:lilian.baudry@etu.univ-lyon1.fr) [p2103568]