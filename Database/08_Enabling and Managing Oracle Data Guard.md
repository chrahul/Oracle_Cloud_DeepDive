
---

## **Title: Step-by-Step Guide to Enabling and Managing Oracle Data Guard in OCI**

---

### **Concept Takeaway**

Oracle Data Guard is a high availability and disaster recovery solution that ensures business continuity by maintaining a real-time copy of the production database called a standby database. It protects against both planned and unplanned outages. The Data Guard environment includes a primary database and one or more standby databases, which operate in mutually exclusive roles. With Oracle Enterprise Edition, users can configure Data Guard using the OCI Console or API. Active Data Guard extends functionality by enabling read-only access on the standby, offloading backups and queries, and supporting features like automatic block repair and application continuity.

Data Guard supports various transport modes and protection levels to balance performance and data safety. These include synchronous and asynchronous transport and protection modes like maximum performance, availability, and protection. Enabling Data Guard through the OCI console is a guided process and requires VCN, subnet, and optionally cross-region peering if required.

---

## **Step-by-Step Guide to Enabling and Managing Oracle Data Guard**

---

### **Step 1: Understand the Role of Data Guard**

- Oracle Data Guard maintains a standby copy of the production database to protect against planned and unplanned outages
- The database operates in one of two roles: Primary or Standby
- The standby database is continuously synchronized with the primary database
- The Data Guard configuration includes one primary and one or more standby databases

---

### **Step 2: Data Guard License and Availability**

- Oracle Enterprise Edition includes physical standby Data Guard in mounted recovery mode
- Data Guard is not available for Oracle Standard Edition
- Active Data Guard requires the Enterprise Edition Extreme Performance license
- Active Data Guard supports features such as read-only standby, real-time queries, and offloaded backups

---

### **Step 3: Cloud Network Topology Considerations**

#### **Within a Single Region**

- Primary and standby must use the same Virtual Cloud Network
- Recommended to place primary and standby in separate Availability Domains for better fault isolation
- Same database name can be used, but database unique name must be different

#### **Across Regions**

- Use Remote VCN Peering between the VCNs of the two regions
- Ensure latency and performance from the application and on-premises data centers meet business needs
- Set up ingress and egress rules in security lists for both primary and standby subnets to allow TCP communication

---

### **Step 4: Key Benefits of Data Guard**

- Continuous service using switchover and failover operations
- Data protection against physical corruption and user errors
- Eliminates idle standby by enabling reporting or backups on standby
- Flexible configurations with multiple protection modes
- Centralized control through OCI Console or API

---

### **Step 5: Active Data Guard Benefits**

- Enables read-only real-time access to standby for reporting
- Supports ad hoc queries and analytical workloads
- Offloads backups from the primary to the standby
- Supports snapshot standby for temporary read-write access
- Improves overall resource utilization

---

### **Step 6: Role Transition Operations**

- **Switchover**: Planned role reversal. Primary becomes standby and standby becomes primary. Used during patching or maintenance
- **Failover**: Unplanned role reversal. Used during catastrophic failure. Standby takes over as primary
- **Fast Start Failover**: Enables automatic failover to a synchronized standby
- **Reinstate**: Reintegrates a failed primary as standby after it is repaired

---

### **Step 7: Data Guard Protection Modes**

- **Maximum Performance**: Default. Uses asynchronous redo transport. Prioritizes performance over zero data loss
- **Maximum Availability**: Uses synchronous transport. Maintains high data protection without impacting primary availability
- **Maximum Protection**: Not mentioned here but is the highest level of data safety and requires standby acknowledgment before committing transactions

---

### **Step 8: Transport Configurations**

- **SYNC AFFIRM**: Redo is written to disk on standby before acknowledgment is sent to primary. Offers highest safety but may impact performance
- **SYNC NOAFFIRM**: Redo is received by standby but not written to disk before acknowledgment. Improves performance but can result in data loss during double failure

---

### **Step 9: Impact of Failures Based on Transport Mode**

- In SYNC AFFIRM mode, there is no data loss even if both primary and standby are lost temporarily
- In SYNC NOAFFIRM mode, there may be some data loss in the event of a simultaneous failure

---

### **Step 10: Enabling Data Guard using OCI Console**

1. Login to OCI Console
2. Navigate to the Oracle Base Database Service section
3. Click on the name of the DB System you want to protect
4. Select the database name to open the Database Details page
5. In the database information section, locate the Data Guard section
6. The status will show as Not Enabled
7. On the left side, under Resources, click on Data Guard Associations
8. Click the Enable Data Guard button
9. Follow the workflow to enter peer DB System details for standby database
10. A new DB System will be created for the standby role

---

### **Summary**

Oracle Data Guard provides a robust high availability and disaster recovery solution by maintaining standby copies of the production database. It supports both planned and unplanned failover operations. With Enterprise Edition, you can enable standard Data Guard. With the Extreme Performance license, you can use Active Data Guard for real-time query, reporting, and backups from the standby. You can configure Data Guard either within a region or across regions using the OCI console or APIs. The solution is flexible, offers centralized control, and supports multiple protection modes and transport options to meet performance and safety needs.

---

