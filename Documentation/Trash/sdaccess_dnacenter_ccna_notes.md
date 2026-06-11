# 🌐 Software-Defined Networking: SD-Access & DNA Center — CCNA Study Notes

> **Exam Topics:** 6.3 and 6.4 — SDN architecture, Cisco SD-Access, DNA Center
> **Scope:** Conceptual understanding — no hands-on SDN configuration required for CCNA.

---

## ⚡ Key Takeaways

- SDN centralizes the control plane into a **controller**. Three SDN architecture layers: **Application → Control → Infrastructure**.
- **Underlay** = physical network of switches and connections (provides IP connectivity, e.g., via IS-IS).
- **Overlay** = virtual network of tunnels built on top of the underlay (VXLAN tunnels in SD-Access).
- **Fabric** = underlay + overlay combined — the complete SD-Access network.
- Three SD-Access switch roles: **Edge node** (connects end hosts), **Border node** (connects outside the fabric), **Control node** (runs LISP for the control plane).
- SD-Access uses three key protocols: **LISP** (control plane), **VXLAN** (data plane / tunnels), **Cisco TrustSec** (policy / QoS / security).
- In an optimal SD-Access underlay (greenfield): all links are **Layer 3**, **IS-IS** is the routing protocol, **no STP**, and **access switches are the default gateway** (routed access layer).
- **DNA Center** is the SDN controller for SD-Access AND can be used as a general network management platform in traditional networks.
- DNA Center enables **intent-based networking (IBN)** — engineer states the desired behavior, DNA Center handles the implementation.
- DNA Center's southbound interface supports: **NETCONF, RESTCONF, SSH, Telnet, SNMP**.

---

## 🔄 SDN Review

**Software-Defined Networking (SDN)** centralizes the control plane into a software **controller**.

| Traditional (Distributed) | SDN (Centralized) |
|---|---|
| Each device runs its own control plane | Control plane functions centralized in the controller |
| Devices use OSPF to share routing info with each other | Devices share info with the controller, which calculates routes |
| Policies (ACLs, etc.) configured per-device | Policies defined centrally, pushed to devices |

**SDN interfaces:**
- **Southbound Interface (SBI)** — controller ↔ network devices
- **Northbound Interface (NBI)** — apps/scripts ↔ controller (REST API)

---

## 🏗️ SDN Architecture Layers

> These are SDN-specific layers — not the OSI model.

| Layer | What's in it | Description |
|---|---|---|
| **Application layer** (top) | Scripts, apps, tools | Communicates desired network behavior to the controller |
| **Control layer** (middle) | SDN controller | Receives and processes instructions; houses the centralized control plane |
| **Infrastructure layer** (bottom) | Network devices (switches, routers) | Responsible for actually forwarding traffic |

---

## 🧩 Cisco SDN Solutions (Overview)

| Solution | Purpose |
|---|---|
| **SD-Access** | Automates **campus LANs** (wired + wireless office networks) |
| **ACI** (Application Centric Infrastructure) | Automates **data center networks** (uses spine-leaf architecture) |
| **SD-WAN** | Automates **WAN connections** |

---

## 📐 SD-Access Architecture

**Cisco SD-Access** = Cisco's SDN solution for campus LANs.
**Controller:** Cisco **DNA Center** (Digital Network Architecture Center) sits in the control layer.

```
┌──────────────────────────────────┐
│      Application Layer            │  Scripts, apps, DNA Center GUI
└──────────────┬───────────────────┘
               │ NBI (REST API)
┌──────────────▼───────────────────┐
│         Control Layer             │  DNA Center
└──────────────┬───────────────────┘
               │ SBI (NETCONF, RESTCONF, SSH, etc.)
┌──────────────▼───────────────────┐
│      Infrastructure Layer         │  Campus LAN switches (SD-Access fabric)
└──────────────────────────────────┘
```

---

## 🔻 SD-Access Underlay

> The **underlay** is the **underlying physical network** — the switches and their connections that provide IP connectivity.

### Underlay in a Greenfield Deployment (DNA Center configures it)

| Feature | Value |
|---|---|
| All switch links | **Layer 3** (routed ports — no Layer 2) |
| Routing protocol | **IS-IS** |
| STP required? | ❌ No — no Layer 2 loops possible |
| FHRP required? | ❌ No |
| Default gateway | **Edge nodes (access switches)** — "routed access layer" |

### Traditional LAN vs. SD-Access Underlay

| Traditional LAN | SD-Access Underlay |
|---|---|
| STP used to prevent Layer 2 loops | No STP needed — all links are Layer 3 |
| HSRP/VRRP at distribution layer for redundant gateway | Edge switches ARE the default gateway |
| OSPF typically used for routing | IS-IS used for routing |

### Three Switch Roles in SD-Access

| Role | Description |
|---|---|
| **Edge node** | Connects to end hosts (like a traditional access layer switch) |
| **Border node** | Connects to devices outside the SD-Access domain (e.g., WAN router) |
| **Control node** | Runs **LISP** for control plane functions |

> ⚠️ There is no "management node" — a common distractor answer.

### Brownfield vs. Greenfield

| Type | Description |
|---|---|
| **Greenfield** | Brand-new network built for SD-Access. DNA Center configures the optimal underlay. |
| **Brownfield** | SD-Access added onto an existing network. DNA Center does NOT configure the underlay (too risky for production). |

---

## 🔼 SD-Access Overlay

> The **overlay** is the **virtual network** built on top of the physical underlay using tunnels.

### Three Key Protocols

| Protocol | Role | Details |
|---|---|---|
| **LISP** (Locator ID Separation Protocol) | **Control plane** | Maintains mappings of EIDs → RLOCs. DNS-like system for locating hosts. |
| **VXLAN** (Virtual Extensible LAN) | **Data plane** | Creates the tunnels that carry traffic. "Extensible" = supports many features. |
| **Cisco TrustSec (CTS)** | **Policy** | QoS and security policy enforcement across the fabric. |

### LISP Terms

| Term | Meaning |
|---|---|
| **EID** (Endpoint Identifier) | Identifies an end host connected to an edge switch |
| **RLOC** (Routing Locator) | Identifies the edge switch used to reach that end host |

### How VXLAN + LISP Work Together (Example)

```
1. PC2 (connected to SW2) registers with SW3 (control node): "PC2 is reachable via SW2"
2. PC1 wants to send traffic to PC2 → sends to default gateway SW1
3. SW1 asks SW3: "How do I reach PC2?"
4. SW3 replies: "PC2 is reachable via SW2"
5. SW1 forwards traffic over a VXLAN tunnel to SW2 → SW2 delivers to PC2
```

---

## 🔷 Fabric = Underlay + Overlay

```
Fabric = Underlay (physical switches + connections) + Overlay (VXLAN tunnels)
```

| Term | Definition |
|---|---|
| **Underlay** | Physical network providing IP connectivity |
| **Overlay** | Virtual tunnel network built on top of the underlay |
| **Fabric** | The complete SD-Access network = underlay + overlay |

---

## 🖥️ Cisco DNA Center

**DNA Center** has two roles:
1. **SDN controller** for SD-Access
2. **General network management platform** for traditional networks (without SD-Access)

> DNA Center runs on **Cisco UCS server hardware** and exposes a **REST API** (northbound).

### Southbound Interface Protocols

- NETCONF
- RESTCONF
- SSH
- Telnet
- SNMP

### Intent-Based Networking (IBN)

> Engineer expresses **desired network behavior** → DNA Center translates it into device configurations.

Example: Instead of writing complex ACLs, define group-based policies:
- "Developers group can access Test_Servers"
- "Guest group cannot access any internal servers"

DNA Center implements the required policies across the entire fabric automatically.

### DNA Center GUI Sections

| Section | Purpose |
|---|---|
| **Design** | Build network hierarchy, manage IPs, subnets, DHCP, DNS |
| **Policy** | Define group-based access control and QoS policies |
| **Provision** | Manage device inventory, add new devices, assign to sites |
| **Assurance** | Monitor device health, performance, and network status |

---

## ⚖️ DNA Center vs. Traditional Network Management

| Aspect | Traditional Management | DNA Center Management |
|---|---|---|
| **Configuration method** | One device at a time via SSH/console | Centrally managed from DNA Center GUI or REST API |
| **New device deployment** | Manual pre-configuration before deployment | Devices auto-receive configs from DNA Center |
| **Policy management** | Distributed — per-device ACLs, manual effort | Centralized intent-based policies |
| **Software updates** | Manual, per-device | Centrally managed; DNA Center monitors for new versions and updates devices |
| **Error risk** | High — manual effort = more human error | Lower — automation reduces configuration mistakes |
| **Deployment speed** | Slow — manual work required | Fast — automated provisioning |
| **Compliance visibility** | Limited | DNA Center flags non-compliant software versions and security advisories |

---

## 📋 Key Terms to Memorize

| Term | Definition |
|---|---|
| **SDN** | Software-Defined Networking — centralizes the control plane into a controller |
| **Underlay** | Physical network of devices and connections (provides IP connectivity) |
| **Overlay** | Virtual tunnel network built on top of the underlay |
| **Fabric** | Underlay + overlay combined |
| **Edge node** | SD-Access switch that connects to end hosts |
| **Border node** | SD-Access switch that connects to devices outside the fabric |
| **Control node** | SD-Access switch that runs LISP for control plane functions |
| **LISP** | Control plane protocol — maps EIDs (host identifiers) to RLOCs (switch locators) |
| **VXLAN** | Data plane protocol — creates virtual tunnels in the overlay |
| **Cisco TrustSec** | Provides QoS and security policy enforcement in SD-Access |
| **DNA Center** | Cisco's SDN controller for SD-Access; also a general network management platform |
| **IBN** | Intent-Based Networking — engineer specifies desired behavior, controller implements it |
| **Greenfield** | New network built specifically for SD-Access; DNA Center configures the underlay |
| **Brownfield** | Existing network with SD-Access added on top; DNA Center does NOT configure the underlay |
| **Routed access layer** | Access switches act as Layer 3 default gateways for end hosts |
