# Containerlab — Network Infrastructure as Code

🇨🇴 [Español](README.es.md)

Network labs and automation projects built with **Containerlab**, focused on **Infrastructure as Code, Network Automation, NetDevOps and network programmability**.

This repository documents the creation of reproducible network environments using container-based network operating systems and automation tools.

## 🎯 Project Objective

The objective of this repository is to build network laboratories that can be deployed, destroyed and recreated from code.

Instead of manually creating network topologies, the infrastructure is defined using YAML and container technologies, allowing environments to be:

- Reproducible
- Version controlled
- Portable
- Automated
- Easy to deploy and destroy
- Integrated with Network Automation tools

## 🧰 Technology Stack

The repository progressively explores technologies such as:

- Containerlab
- Docker
- Docker Compose
- Nokia SR Linux
- Linux containers
- Alpine Linux
- YAML
- Ansible
- Python
- Git
- Infrastructure as Code
- Network Automation
- NetDevOps

## 🧪 Current Lab

### Lab 1 — Nokia SR Linux

The first topology currently includes:

```text
          ┌─────────────┐
          │    SRL1     │
          │ Nokia SR OS │
          └──────┬──────┘
                 ║
              2 Links
              / LACP /
                 ║
          ┌──────┴──────┐
          │    SRL2     │
          │ Nokia SR OS │
          └─────────────┘

              │       │
              │       │
           Host1     Host2
          Alpine     Alpine
```

### Nodes

- `srl1` — Nokia SR Linux
- `srl2` — Nokia SR Linux
- `host1` — Alpine Linux
- `host2` — Alpine Linux

### Management Network

```text
172.20.20.0/24
```

Containerlab automatically creates and manages the out-of-band management network for the topology.

### Host Networks

```text
host1: 10.10.10.10/24
host2: 10.10.10.20/24
```

The hosts are connected to the SR Linux devices and can be used to validate end-to-end connectivity and networking configurations.

## 📂 Repository Structure

```text
containerlab/
│
├── ansible/
│   ├── group_vars/
│   ├── host_vars/
│   ├── inventories/
│   └── playbooks/
│
├── lab1/
│   ├── docs/
│   ├── outputs/
│   ├── README.md
│   └── topology.yml
│
├── platform/
│   └── docker-compose.yml
│
├── LICENSE
└── README.md
```

### `lab1/`

Contains the Containerlab topology and supporting files for the first network laboratory.

### `ansible/`

Prepared structure for integrating **Ansible-based network automation** with the Containerlab environments.

### `platform/`

Supporting container infrastructure managed through Docker Compose.

## ⚙️ Infrastructure as Code Approach

Containerlab allows the entire network topology to be represented as code:

```text
Git Repository
      │
      ▼
 topology.yml
      │
      ▼
 Containerlab
      │
      ▼
Network Infrastructure
      │
      ▼
Automation / Validation
      │
      ▼
Ansible / Python / APIs
```

This makes it possible to create repeatable Network Automation workflows where both the **network infrastructure and its configuration are managed programmatically**.

## 🚀 Basic Containerlab Workflow

Deploy a topology:

```bash
containerlab deploy -t topology.yml
```

- `deploy`: creates the lab defined in the topology.
- `-t`: specifies the topology YAML file.

Inspect the deployed lab:

```bash
containerlab inspect -t topology.yml
```

- `inspect`: shows the nodes, management addresses and state of the lab.
- `-t`: selects the topology to inspect.

Destroy the lab:

```bash
containerlab destroy -t topology.yml
```

- `destroy`: removes the containers and virtual links belonging to the lab.
- `-t`: identifies the topology to remove.

## 🤖 Automation Integration

The repository is designed to progressively integrate Containerlab environments with tools such as:

- Ansible
- Python
- NETCONF
- RESTCONF
- gNMI
- JSON-RPC
- Network APIs
- CI/CD pipelines

The objective is to use Containerlab as a lightweight network development platform for testing automation before applying workflows to larger virtual or physical environments.

## 🔄 NetDevOps Approach

Future labs can progressively introduce workflows such as:

```text
Git
 │
 ▼
Topology Deployment
 │
 ▼
Configuration Automation
 │
 ▼
Pre-checks / Validation
 │
 ▼
Network Tests
 │
 ▼
Post-checks
 │
 ▼
Destroy / Rebuild
```

This provides a practical environment for learning and implementing **Network Infrastructure as Code and NetDevOps principles**.

## 📊 Repository Status

> 🚧 **Continuous Development**

Current focus:

- Containerlab
- Nokia SR Linux
- Infrastructure as Code
- Network Automation
- Ansible integration
- NetDevOps

Additional vendors, topologies, automation workflows and validation tools may be incorporated progressively.

## 🧪 Lab Environment

These environments are intended for laboratory, learning and Network Automation development purposes.

Always validate automation workflows before adapting them to production infrastructure.

## 👨‍💻 Author

**Anderson Martinez Virviescas**

Network Administrator | Network Automation | NetDevOps | DevNet | Linux | Infrastructure Automation

GitHub: [@andersonmavi30](https://github.com/andersonmavi30)

---

> Build it. Automate it. Break it. Rebuild it.
