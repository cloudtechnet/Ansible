# Ansible Playbook for Install httpd and git 

To create an Ansible playbook for installing `httpd` (Apache) and `git` services on an Amazon Linux instance, you can follow these steps:

### 1. **Create the Ansible Playbook**

First, create a file named `install_httpd_git.yml`:

```yaml
---
- name: Install httpd and git on Amazon Linux
  hosts: amazon_linux
  become: yes

  tasks:
    - name: Install httpd
      yum:
        name: httpd
        state: present

    - name: Ensure httpd is started and enabled
      service:
        name: httpd
        state: started
        enabled: yes

    - name: Install git
      yum:
        name: git
        state: present
```

### 2. **Define Your Inventory File**

Next, create an inventory file to specify your Amazon Linux hosts. Name it `hosts`:

```ini
[amazon_linux]
your_amazon_linux_host_ip_or_hostname
```

Replace `your_amazon_linux_host_ip_or_hostname` with the actual IP address or hostname of your Amazon Linux instance.

### 3. **Run the Playbook**

Finally, run the playbook using the following command:

```bash
ansible-playbook -i hosts install_httpd_git.yml
```

### Explanation:

1. **`hosts: amazon_linux`**: Specifies the target hosts defined in the inventory file under the `amazon_linux` group.
2. **`become: yes`**: Ensures that the tasks are run with `sudo` privileges.
3. **`yum:`**: This module is used to install packages on Red Hat-based systems, including Amazon Linux.
4. **`service:`**: This module is used to start and enable the `httpd` service.

This playbook will install `httpd` and `git`, start the `httpd` service, and ensure it is enabled to start at boot on an Amazon Linux instance.