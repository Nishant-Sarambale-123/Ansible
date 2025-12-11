Here is a **complete, clean, organized Ansible command cheat-sheet** you can directly use for your notes.
(All commonly used commands are included.)

---

# ✅ **ANSIBLE COMMAND CHEAT-SHEET**

---

## 🟦 **1. Check Ansible Version**

```
ansible --version
ansible-playbook --version
```

---

## 🟩 **2. Test Connectivity (Ping Module)**

```
ansible all -m ping
ansible webservers -m ping
```

---

## 🟧 **3. Run Ad-hoc Commands**

### 🔹 **Run a shell/command**

```
ansible all -m command -a "uptime"
ansible all -m shell -a "df -h"
```

### 🔹 **Using `become`**

```
ansible all -m shell -a "systemctl status nginx" -b
```

---

## 🟥 **4. Copy Files**

```
ansible all -m copy -a "src=/tmp/test dest=/tmp/"
```

### Copy with permissions

```
ansible all -m copy -a "src=file dest=/etc/file mode=0644 owner=root group=root"
```

---

## 🟦 **5. File Module**

```
ansible all -m file -a "path=/tmp/mydir state=directory"
ansible all -m file -a "path=/tmp/myfile state=absent"
```

---

## 🟪 **6. Package Management**

### **YUM / DNF (RHEL/CentOS/Amazon Linux)**

```
ansible all -m yum -a "name=httpd state=present"
ansible all -m yum -a "name=httpd state=latest"
```

### **APT (Ubuntu/Debian)**

```
ansible all -m apt -a "name=nginx state=present update_cache=yes"
```

---

## 🟫 **7. Service Management**

```
ansible all -m service -a "name=httpd state=started"
ansible all -m service -a "name=nginx state=restarted"
ansible all -m service -a "name=nginx state=stopped enabled=no"
```

---

## 🟩 **8. User & Group Management**

```
ansible all -m user -a "name=john state=present"
ansible all -m group -a "name=devops state=present"
```

---

## 🔵 **9. Gather Facts**

```
ansible all -m gather_facts
```

---

# 🟨 **10. Inventory Commands**

### Show inventory in JSON format

```
ansible-inventory -i inventory.ini --list
```

### Show inventory tree graph

```
ansible-inventory -i inventory.ini --graph
```

---

# 🟦 **11. Run Playbooks**

### Basic playbook run

```
ansible-playbook site.yml
```

### With inventory

```
ansible-playbook -i inventory.ini site.yml
```

### Extra variables

```
ansible-playbook site.yml -e "version=1.2 env=prod"
```

### Limit run to one host

```
ansible-playbook site.yml --limit web1
```

### Check/ Dry run (no changes)

```
ansible-playbook site.yml --check
```

### Syntax check

```
ansible-playbook site.yml --syntax-check
```

### Tags

```
ansible-playbook site.yml --tags "install"
ansible-playbook site.yml --skip-tags "config"
```

---

# 🟥 **12. Vault (Secrets Encryption)**

### Create encrypted file

```
ansible-vault create secrets.yml
```

### Encrypt existing file

```
ansible-vault encrypt file.yml
```

### Decrypt

```
ansible-vault decrypt file.yml
```

### Edit encrypted file

```
ansible-vault edit secrets.yml
```

### Run playbook with vault password

```
ansible-playbook site.yml --ask-vault-pass
```

---

# 🟩 **13. Ansible Galaxy**

```
ansible-galaxy init myrole
ansible-galaxy install geerlingguy.nginx
```

---

# 🟪 **14. Roles Directory Structure**

```
roles/
  myrole/
    tasks/
    handlers/
    templates/
    vars/
    defaults/
    files/
    meta/
```

---

# 🟧 **15. Useful Options**

### Become (sudo)

```
ansible-playbook site.yml --become
```

### Verbose Mode

```
ansible -m ping all -vvv
```

---

# 🟦 **16. Ad-hoc File/Dir Ownership**

```
ansible all -m file -a "path=/var/www state=directory owner=nginx group=nginx mode=0755"
```

---

# 🟫 **17. Fetch Files From Remote**

```
ansible all -m fetch -a "src=/var/log/messages dest=/tmp/logs/"
```

---

# 🟥 **18. Template (Jinja2)**

```
ansible all -m template -a "src=nginx.conf.j2 dest=/etc/nginx/nginx.conf"
```

---

# 🟨 **19. Reboot Hosts**

```
ansible all -m reboot
```

---

# 🟩 **20. Check Host Information**

```
ansible all -m setup
```

---

# 🟦 COMPLETE ANSIBLE COMMAND NOTE READY ✔

If you want, I can also provide this as:

✅ **PDF**
✅ **Markdown note**
✅ **One-page cheat sheet**

Just tell me.
