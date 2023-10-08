Creating a README for your Ansible configuration script is a great way to help users understand how it works and how to use it. Below is a template for a README file that explains your Ansible script for setting up Node.js, Rust, and zsh, with the entry point being `dev.ansible.yml`.

---

# Ansible Configuration for Node.js, Rust, and zsh Setup

This Ansible configuration script is designed to automate the setup of Node.js, Rust, and the zsh shell on your system. This README provides instructions on how to use the script and explains its purpose.

## Prerequisites

Before using this Ansible script, ensure that you have the following prerequisites installed on your system:

- [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)
- [Python](https://www.python.org/downloads/) (required for Ansible)
- A target machine (local or remote) where you want to set up Node.js, Rust, and zsh.

## Usage

1. Clone this repository to your local machine or download the Ansible playbook:

   ```bash
   git clone https://github.com/carls-rodrigues/dev-environment
   ```

2. Navigate to the directory where the playbook is located:

   ```bash
   cd dev-environment
   ```

3. Edit the `dev.ansible.yml` file to customize the installation as needed. You can configure:

   - Node.js version.
   - Rust version.
   - zsh configuration.

4. Run the Ansible playbook using the following command:

   ```bash
   ansible-playbook dev.ansible.yml -K
   ```

   - `-K` will prompt you for the sudo password if necessary.

5. Wait for the playbook to complete. Ansible will handle the installation of Node.js, Rust, and zsh based on your configuration.

6. Once the playbook finishes, you should have Node.js, Rust, and zsh installed and configured as specified in `dev.ansible.yml`.

## Configuration (dev.ansible.yml)

The `dev.ansible.yml` file is the main configuration file for this Ansible script. It allows you to specify the following:

- `nodejs_version`: Set the desired version of Node.js.
- `rust_version`: Set the desired version of Rust.
- `zsh_config`: Configure zsh settings, such as aliases, themes, and plugins.

Here's an example of how to configure `dev.ansible.yml`:

```yaml
---
- name: Dev Environment Setup
  hosts: localhost
  become: true
  
  pre_tasks:
    - name: Update cache
      apt:
        update_cache: true
      tags:
        - node
        - zsh
        - rust
  tasks:
    - include:
      - node
      - zsh
      - rust
```

## License

This Ansible script is provided under the [MIT License](LICENSE).