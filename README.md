<div align="center">

<!-- 🎞️ Swap this for your own banner/GIF (e.g. a terminal recording from asciinema or a .gif in docs/) -->
<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=30&duration=3000&pause=800&color=EE0000&center=true&vCenter=true&width=600&lines=%E2%9A%99%EF%B8%8F+Ansible+Role;Automate+Everything;Deploy+in+Seconds" alt="Typing banner" />

# ⚙️ Role Name

### 🚀 *A brief description of the role goes here.*

[![Ansible](https://img.shields.io/badge/Ansible-EE0000?style=for-the-badge&logo=ansible&logoColor=white)](https://www.ansible.com/)
[![Galaxy](https://img.shields.io/badge/Galaxy-Role-5BBDAF?style=for-the-badge&logo=ansible&logoColor=white)](https://galaxy.ansible.com/)
[![Python](https://img.shields.io/badge/Python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)](https://www.python.org/)
[![License](https://img.shields.io/badge/License-BSD-blue?style=for-the-badge)](#-license)

<!-- 🎥 Optional demo GIF — record with `asciinema` + `agg`, or a screen recorder -->
<img src="docs/demo.gif" alt="Role demo" width="700" />

</div>

---

## 📖 Table of Contents

| 🔖 | Section |
|----|---------|
| 📋 | [Requirements](#-requirements) |
| 🎛️ | [Role Variables](#%EF%B8%8F-role-variables) |
| 🔗 | [Dependencies](#-dependencies) |
| 🎬 | [Example Playbook](#-example-playbook) |
| ▶️ | [Usage](#%EF%B8%8F-usage) |
| 📄 | [License](#-license) |
| 👤 | [Author Information](#-author-information) |

---

## 📋 Requirements

> ⚠️ Anything **not** shipped with Ansible itself belongs here.

| ✔️ | Requirement | 💬 Notes |
|----|-------------|----------|
| 🧰 | **Ansible** `>= 2.9` | Core engine |
| 🐍 | **Python** `>= 3.8` | On the control node |
| 📦 | **boto3 / botocore** | Required if this role uses the **EC2** module |
| 🔑 | **AWS credentials** | Via `aws configure` or environment variables |

```bash
pip install boto3 botocore
```

---

## 🎛️ Role Variables

> 🧩 Variables from `defaults/main.yml`, `vars/main.yml`, and role parameters.

### 🟢 Defaults — `defaults/main.yml`

| 🏷️ Variable | 📝 Description | ⚙️ Default |
|-------------|----------------|-----------|
| `role_enabled` | Toggle the role on/off | `true` |
| `role_version` | Version of the package to install | `"latest"` |
| `role_port` | Port the service listens on | `8080` |

### 🔒 Vars — `vars/main.yml`

| 🏷️ Variable | 📝 Description | ⚙️ Value |
|-------------|----------------|----------|
| `role_package_name` | OS package name | `"my-package"` |
| `role_service_name` | systemd service name | `"my-service"` |

### 🌐 External / Inherited Variables

> 📥 Values read from `hostvars`, `group_vars`, or other roles.

| 🏷️ Variable | 📦 Source | 📝 Purpose |
|-------------|-----------|-----------|
| `ansible_host` | inventory | Target host address |
| `env` | `group_vars/all` | Deployment environment |

---

## 🔗 Dependencies

> 🧱 Other Galaxy roles this one relies on.

```yaml
dependencies:
  - role: username.common
    vars:
      common_setting: true
  - role: username.firewall
```

| 🧩 Role | 📝 Why it's needed |
|---------|-------------------|
| `username.common` | Base packages & system tuning |
| `username.firewall` | Opens the required ports |

> ✅ If there are **no dependencies**, just say so — it's a feature! 🎉

---

## 🎬 Example Playbook

```yaml
---
- hosts: servers
  become: true
  roles:
    - role: username.rolename
      vars:
        x: 42
        role_port: 9090
        role_version: "1.2.3"
```

### 🧪 Minimal example

```yaml
- hosts: servers
  roles:
    - { role: username.rolename, x: 42 }
```

---

## ▶️ Usage

### 1️⃣ Install the role
```bash
ansible-galaxy install username.rolename
```

### 2️⃣ Run the playbook
```bash
ansible-playbook -i inventory playbook.yml
```

### 3️⃣ Dry run first 👀
```bash
ansible-playbook -i inventory playbook.yml --check --diff
```

### 4️⃣ Target specific hosts 🎯
```bash
ansible-playbook -i inventory playbook.yml --limit web01
```

---

## 🗂️ Role Structure

```
📦 rolename
 ┣ 📂 defaults      # 🟢 Default variables (lowest precedence)
 ┣ 📂 vars          # 🔒 Role variables (high precedence)
 ┣ 📂 tasks         # ⚡ Main task list
 ┣ 📂 handlers      # 🔔 Restart / reload handlers
 ┣ 📂 templates     # 📄 Jinja2 templates
 ┣ 📂 files         # 📁 Static files to copy
 ┣ 📂 meta          # 🧾 Galaxy metadata & dependencies
 ┣ 📂 tests         # 🧪 Test playbook & inventory
 ┗ 📜 README.md     # 📖 You are here
```

---

## 🤝 Contributing

🎉 Contributions are welcome!

1. 🍴 Fork it
2. 🌿 `git checkout -b feature/awesome`
3. 💾 `git commit -m "Add awesome feature"`
4. 🚀 `git push origin feature/awesome`
5. 🔃 Open a Pull Request

---

## 📄 License

🛡️ **BSD**

---

## 👤 Author Information

> ✉️ An optional section for the role authors to include contact information or a website.

| 🔗 | Link |
|----|------|
| 👨‍💻 **Author** | Your Name |
| 🐙 **GitHub** | [@username](https://github.com/username) |
| 🌌 **Galaxy** | [username.rolename](https://galaxy.ansible.com/username/rolename) |
| 📧 **Email** | you@example.com |

---

<div align="center">

### ⭐ Found this role useful? Give it a star!

Made with ❤️ and ⚙️ using **Ansible**

</div>
