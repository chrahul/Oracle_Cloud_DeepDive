# **Oracle Base Database Service on Virtual Machine (VM) DB Systems in OCI**:

---

##  **Oracle Base Database Service on VM – Simplified Guide**

Oracle Base Database Service lets you create and manage **full-featured Oracle Databases** in the **Oracle Cloud Infrastructure (OCI)** using **Virtual Machines (VMs)**. It’s great for customers who want more control over their database systems while still taking advantage of cloud automation.

---

###  What is Oracle Base Database Service?

It’s a **co-managed** cloud service:
- **Oracle** manages the infrastructure (hardware, storage, VM hosting).
- **You** manage the database software (like backups, patching, and security) using easy tools provided via OCI Console or APIs.

You get full control over the VM — including **root access** — to customize the database environment as needed.

---

###  Key Features

- Deploy **Oracle Enterprise or Standard Edition** databases.
- Choose **single-instance** or **two-node RAC (Real Application Clusters)** for high availability.
- Supports Oracle DB versions: **19c, 21c, and 23ai**.
- Available globally across **Oracle Cloud regions**.
- Offers **automated lifecycle operations**: provisioning, patching, backup, scaling, and Data Guard.

---

###  Licensing Options

There are two ways to license your database:

| Model | What It Means |
|-------|---------------|
| **License Included (LI)** | Oracle provides the license. Best for new users. Includes features like TDE, tuning packs, and support. |
| **Bring Your Own License (BYOL)** | Use your existing Oracle DB licenses in the cloud. Cost-saving option for customers migrating to OCI. |

With **BYOL**, you even get access to premium features like TDE, Data Masking, and RAC *without needing to separately bring those licenses*.

---

###  Licensing Tiers Explained

| Tier | Key Features |
|------|--------------|
| **Standard Edition 2** | Basic DB features, up to 3 pluggable DBs. |
| **Enterprise Edition (EE)** | Adds Data Guard, tuning, and diagnostics. |
| **EE High Performance** | Includes partitioning, compression, and advanced security. |
| **EE Extreme Performance** | Includes everything + RAC, Active Data Guard, In-Memory DB. |

>  To use **RAC or Active Data Guard**, you must select **Extreme Performance** tier.

---

###  Compute Options (Shapes)

Oracle offers 4 types of VM shapes (machine types) based on your performance and budget:

| Shape | Highlights |
|-------|------------|
| **Ampere (A1)** | Low-cost ARM-based, single-node only, up to 57 OCPUs. Memory: 8 GB per OCPU. |
| **AMD Flex** | Supports single or two-node RAC. OCPUs: 1–64. Memory: 16 GB per OCPU. |
| **Intel Flex** | Also supports RAC. OCPUs: 1–32. Memory: 16 GB per OCPU. |
| **Fixed Shapes (older)** | Limited options. Scaling requires resizing the VM. |

Network speed increases with more OCPUs — up to 40 Gbps.

---

###  Storage Options

Two choices for storage management:

| Type | Description |
|------|-------------|
| **ASM (Automatic Storage Management)** | Default and required for RAC. Oracle manages storage distribution. |
| **LVM (Logical Volume Manager)** | Available for single-node. Simpler, quicker provisioning. |

- You can scale storage **online up to 80 TB**.
- Backups go to **Object Storage** or **Recovery Service** (which provides enhanced features at the same price).

---

###  High Availability & Disaster Recovery

Oracle uses the following for high availability (HA):

- **Fault Domains**: VMs are placed on separate hardware to avoid single point of failure.
- **Availability Domains**: Spread resources across data centers.
- **Regions**: Use **Data Guard** to replicate your database to another region for DR.

Two-node RAC deployments place each VM in a different fault domain for HA.

---

###  Security: Built-in and Deep

Oracle follows a **Defense-in-Depth** model:
- **TDE** (Transparent Data Encryption) – Encrypts data at rest.
- **Data Redaction & Masking** – Show only necessary data.
- **Oracle Vault** – Manages encryption keys securely.
- **Database Vault** – Prevents DBAs from accessing sensitive data.
- **Database Firewall** – Controls allowed SQL queries.
- **Data Safe** – Detects risks, finds sensitive data, audits activity. Included for free.

Also, OCI uses:
- **Secure VCNs**, **Token-based SSH**, and **minimum OS packages** for safety.

---

###  Automation Benefits

Cloud automation helps you:
- Avoid manual mistakes.
- Reduce DBA workload.
- Quickly provision new DB systems.
- Maintain **best practices** by default.

Automation covers:
- Provisioning
- Patching
- Scaling
- Backups
- Data Guard setup

---

###  Summary Table – What You Control vs. What Oracle Manages

| Responsibility | Oracle | You |
|----------------|--------|-----|
| Infrastructure (network, hardware) |  |  |
| VM OS (patching, config) |  |  |
| Oracle DB (install, backup, patching) |  |  |
| Automation tools & console |  |  |
| Data & schema |  |  |

---

###  Final Thoughts

The **Oracle Base Database Service on VM** is best suited for:
- Users who want **full control** over their Oracle DB
- Companies migrating from **on-prem Oracle databases**
- Those needing **custom configurations**, **RAC**, or **enterprise features**

It's **more flexible than Autonomous DB** but requires a bit more management.

---

