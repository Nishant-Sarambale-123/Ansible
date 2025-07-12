Here's a **comprehensive guide to Ansible Interview Preparation**, including **top interview questions**, **scenario-based questions**, **conceptual explanations**, and links to official documentation. This covers beginner to advanced level to help you **crack Ansible interviews with confidence**.

---

# ✅ Ansible Interview Preparation Guide

---

## 🔹 Sections Covered:

1. 🔧 **Basic Concepts**
2. 📂 **Inventory, Modules, Ad-Hoc**
3. 📘 **Playbooks, Roles, Handlers**
4. 🔐 **Vault, Variables, Facts**
5. 🔁 **Loops, Conditions, Templates**
6. 🎯 **Best Practices & Real-world Scenarios**
7. 🧪 **Testing, Linting, Idempotency**
8. 🔧 **Plugins, Lookups, Filters**
9. 🚀 **CI/CD, Ansible Tower**
10. 💼 **Scenario-Based Interview Q\&A**

---

## 🔹 1. Basic Questions

### ❓ Q1: What is Ansible?

**Answer:**
Ansible is an **agentless, open-source automation tool** used for **configuration management**, **application deployment**, and **orchestration**.

📘 [Ansible Intro Docs](https://docs.ansible.com/ansible/latest/user_guide/intro.html)

---

### ❓ Q2: How is Ansible different from Puppet, Chef?

| Feature   | Ansible     | Puppet   | Chef    |
| --------- | ----------- | -------- | ------- |
| Language  | YAML (easy) | DSL      | Ruby    |
| Agentless | ✅ Yes       | ❌ No     | ❌ No    |
| Setup     | Simple      | Moderate | Complex |

📘 [Comparison Article](https://www.redhat.com/en/topics/automation/ansible-vs-puppet-vs-chef)

---

## 🔹 2. Inventory, Modules & Ad-Hoc Commands

### ❓ Q3: What is an Inventory in Ansible?

**Answer:**
An inventory is a file that defines the hosts (and groups) Ansible manages.

```ini
[web]
web1 ansible_host=192.168.1.10
```

📘 [Inventory Docs](https://docs.ansible.com/ansible/latest/user_guide/intro_inventory.html)

---

### ❓ Q4: What is an Ad-Hoc command?

```bash
ansible all -m ping
ansible web -a "df -h"
```

**Used for:** One-liner tasks without writing playbooks.

📘 [Ad-Hoc Commands](https://docs.ansible.com/ansible/latest/user_guide/intro_adhoc.html)

---

### ❓ Q5: What are Ansible modules?

**Answer:**
Modules are **discrete units of work** used in playbooks or ad-hoc tasks. Examples: `yum`, `apt`, `service`, `copy`.

📘 [Module Index](https://docs.ansible.com/ansible/latest/collections/index_module.html)

---

## 🔹 3. Playbooks, Roles, Handlers

### ❓ Q6: What is a playbook?

**Answer:**
A YAML file containing a list of tasks to run on a group of hosts.

```yaml
- hosts: web
  tasks:
    - name: Install nginx
      apt:
        name: nginx
        state: present
```

📘 [Playbook Guide](https://docs.ansible.com/ansible/latest/user_guide/playbooks.html)

---

### ❓ Q7: What is the use of a role?

**Answer:**
A role allows you to **group tasks, vars, templates, handlers**, etc., in a **structured and reusable way**.

📘 [Roles Guide](https://docs.ansible.com/ansible/latest/user_guide/playbooks_reuse_roles.html)

---

### ❓ Q8: What is a handler?

**Answer:**
A handler is a task that only runs when **notified** by another task (e.g., service restart).

---

## 🔹 4. Vault, Variables, Facts

### ❓ Q9: How do you secure sensitive data in Ansible?

**Answer:**
Use **Ansible Vault** to encrypt secrets like passwords or tokens.

```bash
ansible-vault encrypt secrets.yml
```

📘 [Vault Docs](https://docs.ansible.com/ansible/latest/user_guide/vault.html)

---

### ❓ Q10: What are facts in Ansible?

**Answer:**
Facts are **system properties** (e.g., IP, OS, hostname) gathered via the `setup` module.

```yaml
ansible_facts['default_ipv4']['address']
```

📘 [Facts Docs](https://docs.ansible.com/ansible/latest/user_guide/playbooks_variables.html#facts)

---

## 🔹 5. Loops, Conditions, Templates

### ❓ Q11: How do you use loops?

```yaml
- name: Install packages
  apt:
    name: "{{ item }}"
    state: present
  loop:
    - nginx
    - curl
```

---

### ❓ Q12: How do you apply conditionals?

```yaml
when: ansible_os_family == "Debian"
```

---

### ❓ Q13: What is a Jinja2 template?

**Answer:**
A templating system used to dynamically generate files using variables.

📘 [Jinja2 Filters](https://jinja.palletsprojects.com/en/3.1.x/templates/#list-of-builtin-filters)

---

## 🔹 6. Real-World & Best Practices

### ❓ Q14: Why should we use roles?

* Clean, reusable
* Encourages modularity
* Scalable for teams

---

### ❓ Q15: How do you manage different environments (dev, prod)?

* Use separate inventories: `inventories/dev`, `inventories/prod`
* Use `group_vars` and `host_vars`

---

## 🔹 7. Testing, Idempotency, Linting

### ❓ Q16: What is idempotency in Ansible?

**Answer:**
Re-running the same playbook results in **no changes** if the system is already in the desired state.

---

### ❓ Q17: What tools are used for Ansible testing?

* `ansible-lint` – for linting YAML and playbooks
* `molecule` – for role testing

---

## 🔹 8. Plugins, Lookups, Filters

### ❓ Q18: What is a lookup?

**Answer:**
Used to fetch external data during runtime.

```yaml
lookup('env', 'HOME')
```

📘 [Lookup Plugins](https://docs.ansible.com/ansible/latest/plugins/lookup.html)

---

### ❓ Q19: What are filters?

Used to transform data (e.g., `upper`, `replace`, `join`).

```yaml
{{ mylist | join(',') }}
```

📘 [Filter Docs](https://docs.ansible.com/ansible/latest/user_guide/playbooks_filters.html)

---

## 🔹 9. CI/CD Integration

### ❓ Q20: How do you integrate Ansible with GitHub Actions?

```yaml
- name: Run Ansible Playbook
  run: ansible-playbook site.yml -i inventory
```

📘 [CI/CD with Ansible](https://docs.ansible.com/ansible/latest/dev_guide/ci_testing.html)

---

### ❓ Q21: How do you use Ansible in Jenkins?

* Use Ansible plugin or shell steps
* Run `ansible-playbook` commands

---

## 🔹 10. Scenario-Based Questions

---

### ❓ Q22: You want to restart a service only when a config file changes. How?

**Answer:**
Use `notify` and `handlers`.

```yaml
- name: Copy config
  copy:
    src: my.conf
    dest: /etc/my.conf
  notify: Restart service

handlers:
  - name: Restart service
    service:
      name: myservice
      state: restarted
```

---

### ❓ Q23: How do you ensure a playbook doesn’t accidentally run on production?

**Answer:**

* Use separate inventory files
* Use `--limit` or tags
* Add safety prompts or approvals in CI/CD

---

### ❓ Q24: You want to reuse a role from Galaxy. How?

```bash
ansible-galaxy install geerlingguy.nginx
```

Then reference in playbook:

```yaml
roles:
  - geerlingguy.nginx
```

📘 [Galaxy Docs](https://galaxy.ansible.com/)

---

### ❓ Q25: How do you debug a playbook?

* Use `-v`, `-vvv` verbosity
* Use `debug` module
* Use `ansible-playbook --check --diff`

---

## 📘 Bonus: Downloadable Resources

| Resource                  | Link                                                                                     |
| ------------------------- | ---------------------------------------------------------------------------------------- |
| All Official Ansible Docs | [https://docs.ansible.com/](https://docs.ansible.com/)                                   |
| Ansible Galaxy Roles      | [https://galaxy.ansible.com/](https://galaxy.ansible.com/)                               |
| Ansible-lint              | [https://github.com/ansible/ansible-lint](https://github.com/ansible/ansible-lint)       |
| Molecule Role Testing     | [https://molecule.readthedocs.io/en/latest/](https://molecule.readthedocs.io/en/latest/) |

---

## ✅ Final Tips for Interviews

* 🧠 Understand **core concepts** deeply (inventory, modules, facts, idempotency)
* 🧪 Practice real-world playbooks on your VM/cloud
* 🧰 Use roles, templates, handlers in projects
* 🔒 Never hardcode passwords — **use Vault**
* 🚀 Be ready to write/play/debug YAML live in interviews
* 🎯 Focus on best practices + CI/CD integration

---

Let me know if you'd like:

* 📥 A **PDF/Notion export** of all notes
* 🚀 Mock interview questions
* 📁 Real-world Ansible project walkthrough

Ready for your next DevOps topic?
