**Title: Step-by-Step Guide to Provision Oracle Base Database Service on OCI**

**Objective:** This document provides a logical, step-by-step guide for provisioning Oracle Base Database Service on a Virtual Machine (VM) in Oracle Cloud Infrastructure (OCI), using concepts familiar to AWS users.

---

### Step 1: Understand OCI Networking (Equivalent to VPC in AWS)

- **VCN (Virtual Cloud Network)**: Equivalent to AWS VPC. It includes subnets, route tables, gateways.
- **Subnets**: Can be regional or specific to an Availability Domain (AD).
- **Gateways**:
  - **Internet Gateway**: For public access.
  - **Service Gateway**: For private access to Oracle services.
  - **DRG (Dynamic Routing Gateway)**: For connecting to on-premises via VPN or FastConnect.

**Action:**
- Create a VCN with CIDR range.
- Create at least one subnet (private recommended).
- Attach an Internet or Service Gateway based on requirement.

---

### Step 2: Set Up IAM (Identity and Access Management)

- **Users**: Individual identities.
- **Groups**: Collection of users.
- **Policies**: Define who can do what on which resources.
- **Compartments**: Logical containers for resources (like AWS resource tagging or projects).

**Action:**
- Create groups such as "DBAdmins".
- Define policies like:
  ```
  Allow group DBAdmins to manage database-family in tenancy
  ```
- Ensure policies are attached to both source and target compartments if resources need to be moved.

---

### Step 3: Prerequisites Before Provisioning

- IAM policies and service limits must be in place.
- SSH Key Pair: Public key (OpenSSH format) required.
- Network setup (VCN, Subnet).
- For 2-node RAC, port 22 should be open in both directions with stateful rules.

---

### Step 4: Launch a Virtual Machine DB System (Console Based)

**Using the OCI Console:**
- Go to https://cloud.oracle.com
- Log in with your account credentials
- Navigate to "Oracle Database" > "Oracle Base Database Service"

**Action:**
- Click "Create DB System"
- Select:
  - Compartment
  - Availability Domain
  - VM Shape (Choose processor type, OCPUs, RAM)
  - Storage type (LVM or ASM), volume size, and performance level
  - License Model (License Included or BYOL)
  - SSH Public Key
  - VCN and Subnet
  - Hostname Prefix
  - DB Version
  - CDB and PDB Name
  - Admin password
- Enable backups (recommended)
- Click "Create DB System"

---

### Step 5: Monitor Provisioning Status

- After creation, the DB System will show status "Provisioning"
- It turns to "Available" when ready
- Other status values: Updating, Stopped, Terminating, Terminated, Failed

---

### Step 6: Tag Your Resources

**Types of Tags:**
- **Defined Tags**: Created and controlled by admin
- **Free-form Tags**: Created by users with resource permissions

**Action:**
- Go to DB System > Add Tags
- Use tags to group, search, and apply policies

---

### Step 7: OS Users on the DB System

**Default OS Users:**
- **opc**: Default SSH login user. Use with sudo to switch to others.
- **oracle**: For DB admin tasks
- **root**: For full system admin
- **grid**: Used in RAC setups (not applicable for single-node LVM-based systems)

**Action:**
- Connect using:
  ```
  ssh -i <private-key> opc@<public-ip>
  ```
- Switch user as needed using sudo su - oracle or sudo su - root

---

### Step 8: Validate SSH Access

- Port 22 must be open on the subnet
- Validate security list or NSG rules

**Action:**
- Test SSH login with:
  ```
  ssh -i <path-to-private-key> opc@<db-system-ip>
  ```

---

### Step 9: Manage the Database

**Tools Available:**
- **OCI Console**
- **OCI CLI**
- **Oracle REST API / SDK**
- **SQL Developer / Enterprise Manager**

---

**Summary:**
You have now learned how to provision a VM-based Oracle Base Database System in OCI, using a process aligned with cloud architecture and governance models familiar from AWS. You also learned about networking, IAM, SSH, tagging, user roles, and monitoring.

For more details, refer to Oracle official docs: https://docs.oracle.com/en/cloud/paas/database.html

