# Ansible Playbook for TestLink

An Ansible playbook of Deploy TestLink with Nginx, PHP 7.4 (php-fpm), and MySQL 5.6+ on CentOS 8.

This is a fork from [galazarevna/ansible_testlink](https://github.com/galazarevna/ansible_testlink) adapted for ZRP usage.

## Requirements

- [Install Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#pip-install)
- Ensure server IP is correct on `hosts` file
- Ensure you have access to the server
- Create a file with the name `vault_password_file` with the password for Ansible Vault to decrypt the `vars/main.vault.yml`
  ```sh
  echo "password" > vault_password_file
  ```

Check the ssh connection to the server

```sh
ansible all -m ping
```

Once you have "pong" in the response you are good to go!

If you need help talk to [ZRP DevOps Team](https://github.com/orgs/zrp/teams/devops)

## Playbook Usage

To run the playbook on your local (vagrant) machine

```sh
ansible-playbook site.yml
```

## What is TestLink?

TestLink is an open-source web-based test management system that facilitates software quality assurance.
The platform offers support for test cases, test suites, test plans, test projects and user management, as well as various reports and statistics.

http://testlink.org/

## What is Ansible?

Ansible is an open-source software provisioning, configuration management, and application-deployment tool enabling infrastructure as code.

https://www.ansible.com/

## What is Vagrant?

Vagrant is an open-source software product for creating and configuring lightweight, reproducible, and portable development environments.

https://www.vagrantup.com/

## Structure

```
ansible_testlink
├── ansible.cfg
├── hosts
├── README.md
├── roles
│   ├── company_settings
│   │   └── tasks
│   │       └── main.yml
│   ├── mysql
│   │   ├── handlers
│   │   │   └── main.yml
│   │   └── tasks
│   │       └── main.yml
│   ├── nginx
│   │   ├── handlers
│   │   │   └── main.yml
│   │   ├── tasks
│   │   │   └── main.yml
│   │   └── templates
│   │       └── nginx.conf.j2
│   ├── php-fpm
│   │   ├── handlers
│   │   │   └── main.yml
│   │   └── tasks
│   │       └── main.yml
│   ├── system
│   │   └── tasks
│   │       └── main.yml
│   └── testlink
│       ├── handlers
│       │   └── main.yml
│       └── tasks
│           └── main.yml
├── site.yml
└── vars
    └── main.yml
```
