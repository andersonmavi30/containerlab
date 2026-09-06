# Containerlab — Infraestructura de Red como Código

🇺🇸 [English](README.md)

Laboratorios de red y proyectos de automatización construidos con **Containerlab**, enfocados en **Infrastructure as Code, Network Automation, NetDevOps y programabilidad de redes**.

Este repositorio documenta la creación de entornos de red reproducibles utilizando sistemas operativos de red basados en contenedores y herramientas de automatización.

## 🎯 Objetivo del proyecto

El objetivo de este repositorio es construir laboratorios de red que puedan desplegarse, destruirse y recrearse desde código.

En lugar de crear topologías manualmente, la infraestructura se define mediante YAML y tecnologías de contenedores, permitiendo que los entornos sean:

- Reproducibles
- Versionados
- Portables
- Automatizables
- Fáciles de desplegar y destruir
- Integrables con herramientas de Network Automation

## 🧰 Stack tecnológico

El repositorio explora progresivamente tecnologías como:

- Containerlab
- Docker
- Docker Compose
- Nokia SR Linux
- Contenedores Linux
- Alpine Linux
- YAML
- Ansible
- Python
- Git
- Infrastructure as Code
- Network Automation
- NetDevOps

## 🧪 Laboratorio actual

### Lab 1 — Nokia SR Linux

La primera topología incluye actualmente:

```text
          ┌─────────────┐
          │    SRL1     │
          │ Nokia SR OS │
          └──────┬──────┘
                 ║
             2 Enlaces
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

### Nodos

- `srl1` — Nokia SR Linux
- `srl2` — Nokia SR Linux
- `host1` — Alpine Linux
- `host2` — Alpine Linux

### Red de gestión

```text
172.20.20.0/24
```

Containerlab crea y administra automáticamente la red de gestión out-of-band de la topología.

### Redes de los hosts

```text
host1: 10.10.10.10/24
host2: 10.10.10.20/24
```

Los hosts están conectados a los dispositivos SR Linux y pueden utilizarse para validar conectividad extremo a extremo y configuraciones de red.

## 📂 Estructura del repositorio

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
├── README.md
└── README.es.md
```

### `lab1/`

Contiene la topología de Containerlab y los archivos de soporte del primer laboratorio de red.

### `ansible/`

Estructura preparada para integrar **automatización de red basada en Ansible** con los entornos de Containerlab.

### `platform/`

Infraestructura de soporte basada en contenedores y administrada mediante Docker Compose.

## ⚙️ Enfoque Infrastructure as Code

Containerlab permite representar toda la topología de red como código:

```text
Repositorio Git
      │
      ▼
 topology.yml
      │
      ▼
 Containerlab
      │
      ▼
Infraestructura de Red
      │
      ▼
Automatización / Validación
      │
      ▼
Ansible / Python / APIs
```

Esto permite crear flujos repetibles de Network Automation donde tanto la **infraestructura de red como su configuración pueden administrarse programáticamente**.

## 🚀 Flujo básico con Containerlab

Desplegar una topología:

```bash
containerlab deploy -t topology.yml
```

- `deploy`: crea el laboratorio definido en la topología.
- `-t`: especifica el archivo YAML de topología.

Inspeccionar el laboratorio desplegado:

```bash
containerlab inspect -t topology.yml
```

- `inspect`: muestra los nodos, direcciones de gestión y estado del laboratorio.
- `-t`: selecciona la topología que se desea inspeccionar.

Destruir el laboratorio:

```bash
containerlab destroy -t topology.yml
```

- `destroy`: elimina los contenedores y enlaces virtuales pertenecientes al laboratorio.
- `-t`: identifica la topología que se desea eliminar.

## 🤖 Integración con automatización

El repositorio está diseñado para integrar progresivamente los entornos de Containerlab con herramientas como:

- Ansible
- Python
- NETCONF
- RESTCONF
- gNMI
- JSON-RPC
- APIs de red
- Pipelines CI/CD

El objetivo es utilizar Containerlab como una plataforma ligera de desarrollo de redes para probar automatización antes de aplicar los flujos a entornos virtuales o físicos de mayor tamaño.

## 🔄 Enfoque NetDevOps

Los futuros laboratorios podrán introducir progresivamente flujos como:

```text
Git
 │
 ▼
Despliegue de Topología
 │
 ▼
Automatización de Configuración
 │
 ▼
Pre-checks / Validación
 │
 ▼
Pruebas de Red
 │
 ▼
Post-checks
 │
 ▼
Destruir / Reconstruir
```

Esto proporciona un entorno práctico para aprender e implementar principios de **Network Infrastructure as Code y NetDevOps**.

## 📊 Estado del repositorio

> 🚧 **Desarrollo continuo**

Enfoque actual:

- Containerlab
- Nokia SR Linux
- Infrastructure as Code
- Network Automation
- Integración con Ansible
- NetDevOps

Se podrán incorporar progresivamente nuevos fabricantes, topologías, flujos de automatización y herramientas de validación.

## 🧪 Entorno de laboratorio

Estos entornos están destinados a laboratorio, aprendizaje y desarrollo de Network Automation.

Valida siempre los flujos de automatización antes de adaptarlos a infraestructura productiva.

## 👨‍💻 Autor

**Anderson Martinez Virviescas**

Network Administrator | Network Automation | NetDevOps | DevNet | Linux | Infrastructure Automation

GitHub: [@andersonmavi30](https://github.com/andersonmavi30)

---

> Build it. Automate it. Break it. Rebuild it.
