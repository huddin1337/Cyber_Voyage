# ⚙️ Configuration Management Tools: Ansible, Puppet & Chef — CCNA Study Notes

> **Exam Topic:** 6.6 — Recognize the capabilities of configuration management mechanisms
> **Scope:** Understand the purpose and basic characteristics of each tool — no hands-on required.

---

## ⚡ Key Takeaways

- **Configuration management tools** (Ansible, Puppet, Chef) automate the configuration and management of large numbers of network devices (and servers/VMs).
- They solve two key problems: **configuration drift** (devices drifting from standard configs over time) and **configuration provisioning** (applying changes at scale).
- All three use **templates + variables** to generate device configurations.
- **Ansible**: Python, agentless, **push** model, uses SSH, files in YAML. Most popular for network devices.
- **Puppet**: Ruby, typically agent-based, **pull** model, TCP 8140, proprietary language, uses Manifests. Server = "Puppet master."
- **Chef**: Ruby, agent-based, **pull** model, TCP 10002, Ruby-based DSL, uses cookbooks/recipes. Least popular for network devices.
- All three use a **client-server model**.
- Puppet and Chef communicate via **HTTP/REST API**. Ansible uses **SSH**.
- All three were originally designed for VM/server management, not specifically for network devices.

---

## 🔀 Why Configuration Management Tools Are Needed

### Problem 1: Configuration Drift

**Configuration drift** = when individual changes made over time cause a device's configuration to deviate from the company's standard templates.

- Every device has some standard config (SNMP, Syslog, AAA, interface settings) and some unique config (hostname, IP addresses).
- Engineers making individual changes (troubleshooting, testing) can cause configs to drift.
- Records of changes and reasons are often not kept — makes it hard to audit or revert.
- Manual approaches (saving config files to a shared folder) don't scale in large networks and depend on engineers remembering to do them.

### Problem 2: Configuration Provisioning

**Configuration provisioning** = how configuration changes are applied to devices (new devices or existing ones).

- Traditional method: SSH/console into each device one-by-one. Not scalable for hundreds/thousands of devices.
- Configuration management tools apply changes at mass scale with minimal time and effort.

### Core Mechanism: Templates + Variables

All three tools use this pattern:

```
Template (shared config structure)  +  Variables (device-specific values)
         ↓
     Generated config → pushed/pulled to device
```

> Example: Template defines OSPF config structure; variable file specifies the process ID, area, and interface for each specific device.

---

## 📊 Comparison Table (Memorize This)

| Feature | **Ansible** | **Puppet** | **Chef** |
|---|---|---|---|
| **Written in** | Python | Ruby | Ruby |
| **Agent required?** | ❌ Agentless | ✅ Agent-based (can be agentless via proxy) | ✅ Agent-based |
| **Model** | **Push** | **Pull** | **Pull** |
| **Protocol** | SSH | HTTP / REST API | HTTP / REST API |
| **Server name** | Control node | Puppet master | Chef server |
| **Config port** | SSH (22) | TCP **8140** | TCP **10002** |
| **File language** | YAML + Jinja2 | Proprietary language | Ruby-based DSL |
| **Key file type** | Playbook | Manifest | Cookbook / Recipe |
| **Popularity (network mgmt)** | ⭐⭐⭐ 1st | ⭐⭐ 2nd | ⭐ 3rd |

---

## 🔵 Ansible

**Owner:** Red Hat | **Language:** Python | **Model:** Push | **Agent:** None (agentless)

### How it works
- The **control node** (Ansible server) connects directly to managed devices via **SSH**.
- No special software needs to be installed on the managed devices — this is the biggest advantage.
- Control node pushes configurations to devices.

### Key Files (all written in YAML, except templates)

| File | Purpose | Format |
|---|---|---|
| **Playbook** | Blueprint of automation tasks — defines logic and actions | YAML |
| **Inventory** | Lists managed devices and their characteristics (role, etc.) | INI or YAML |
| **Template** | Configuration file with placeholders for variables | Jinja2 |
| **Variable file** | Provides values for variables to fill in templates | YAML |

### Ansible Flow
```
Inventory + Templates + Variables → Playbook → SSH → Managed Devices
```

### Why Ansible is Most Popular for Networks
- Agentless → no need for compatible agent software on Cisco devices
- Uses SSH → already supported by virtually all network devices
- YAML → easy to read and write

---

## 🟠 Puppet

**Owner:** Puppet, Inc. | **Language:** Ruby | **Model:** Pull | **Agent:** Typically required

### How it works
- Managed devices have a **Puppet agent** installed, which pulls configurations from the **Puppet master**.
- Not all Cisco devices support a Puppet agent.
- Can run **agentless** using an external proxy agent that connects to devices via SSH on behalf of the Puppet master.
- Clients communicate with Puppet master over **TCP port 8140**.
- Files use a **proprietary language** (not YAML).

### Key Files

| File | Purpose |
|---|---|
| **Manifest** | Defines the **desired configuration state** of a network device |
| **Template** | Helps generate Manifests for devices |

### Puppet Flow
```
Puppet Master (Manifests + Templates) ← Pull ← Puppet Agent (on managed device)
                                      ← Pull ← External Proxy Agent (agentless mode)
```

---

## 🟢 Chef

**Owner:** Progress Software | **Language:** Ruby | **Model:** Pull | **Agent:** Required

### How it works
- Managed devices (**Chef clients**) have a **Chef agent** installed.
- Clients pull configurations from the **Chef server** over **TCP port 10002**.
- Most Cisco devices do NOT support a Chef agent — least popular for network device management.
- Files use a **DSL (Domain-Specific Language) based on Ruby**.
- Admins work on a **Chef workstation** to create cookbooks and recipes, which are stored on the Chef server.

### Key Files (Chef uses a cooking metaphor)

| File | Description |
|---|---|
| **Resource** | Like an ingredient — defines a configuration object managed by Chef |
| **Recipe** | Outlines logic and actions performed on resources |
| **Cookbook** | A set of related recipes grouped together |
| **Run-list** | Ordered list of recipes run to bring a device to the desired state |

### Chef Flow
```
Chef Workstation → creates → Cookbook/Recipe → stored on Chef Server
Chef Client (managed device) ← pulls ← Chef Server (TCP 10002)
```

---

## 🔑 Push vs. Pull Model

| Model | Who initiates the connection | Used by |
|---|---|---|
| **Push** | Server pushes configs to clients | **Ansible** |
| **Pull** | Clients connect to server to receive configs | **Puppet**, **Chef** |

---

## 📋 Key Terms to Memorize

| Term | Definition |
|---|---|
| **Configuration drift** | Deviation of a device's config from the company's standard template over time |
| **Configuration provisioning** | Applying configuration changes to devices (new or existing) |
| **Agentless** | No special software required on managed devices (Ansible) |
| **Agent-based** | Requires specific software installed on managed devices (Puppet, Chef) |
| **Push model** | Server initiates and pushes configs to devices (Ansible) |
| **Pull model** | Managed devices connect to server and pull configs (Puppet, Chef) |
| **Playbook** | Ansible's automation blueprint — written in YAML |
| **Manifest** | Puppet's file defining the desired config state of a device |
| **Cookbook** | Chef's collection of related recipes |
| **Recipe** | Chef's file defining tasks performed on resources |
| **Template** | A configuration structure with variable placeholders (used by all three tools) |
| **Jinja2** | Template language used by Ansible |
| **Control node** | Ansible's server |
| **Puppet master** | Puppet's server |
| **Chef server** | Chef's server |
