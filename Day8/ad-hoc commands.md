# Ansible Ad-hoc commands

Ansible ad-hoc commands are quick, one-time tasks that you can execute directly from the command line without needing to write a full playbook. They are useful for performing simple operations across multiple hosts, like checking system status, copying files, or managing packages.

### 1. **Ping all hosts**

```bash
ansible all -m ping
```

**Explanation:**
- **all**: Targets all hosts listed in your Ansible inventory.
- **-m ping**: Uses the `ping` module to test the connection to each host. It's a simple way to check if Ansible can communicate with all nodes.

### 2. **Check free disk space**

```bash
ansible all -m shell -a "df -h"
```

**Explanation:**
- **-m shell**: Specifies the `shell` module to run a shell command.
- **-a "df -h"**: Passes the command `df -h` to the shell, which displays disk space usage in a human-readable format across all hosts.

### 3. **Install a package**

```bash
ansible webservers -m apt -a "name=nginx state=present"
```

**Explanation:**
- **webservers**: Targets a group of hosts named `webservers` in your inventory.
- **-m apt**: Uses the `apt` module (suitable for Debian/Ubuntu systems).
- **-a "name=nginx state=present"**: Instructs Ansible to ensure that the `nginx` package is installed (`state=present`).

### 4. **Restart a service**

```bash
ansible all -m service -a "name=nginx state=restarted"
```

**Explanation:**
- **-m service**: Uses the `service` module to manage services.
- **-a "name=nginx state=restarted"**: Restarts the `nginx` service on all hosts.

### 5. **Copy a file to multiple hosts**

```bash
ansible all -m copy -a "src=/home/user/file.txt dest=/tmp/file.txt"
```

**Explanation:**
- **-m copy**: Uses the `copy` module to transfer files.
- **-a "src=/home/user/file.txt dest=/tmp/file.txt"**: Copies the file `file.txt` from the local system to `/tmp/file.txt` on all remote hosts.

### Summary
- **Ansible ad-hoc commands** allow you to quickly execute tasks without writing a playbook.
- **Modules** like `ping`, `shell`, `apt`, `service`, and `copy` are used to perform specific tasks.
- These commands are powerful for managing multiple systems at scale, making system administration more efficient.

These examples should give you a good start on how to use Ansible ad-hoc commands effectively!
