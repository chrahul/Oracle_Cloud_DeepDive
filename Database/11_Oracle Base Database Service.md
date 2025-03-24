
---

## **Title: Oracle Base Database Service - Backup and Recovery Guide**

---

### **Concept Takeaway**

This guide covers how to manage database backups and restores for Oracle Base Database Service in Oracle Cloud Infrastructure. Backups can be taken automatically or on-demand. They can be stored in Oracle Object Storage or in Oracle Autonomous Recovery Service. Recovery options include restoring to the latest state, a specific timestamp, or to a specific system change number. Backup operations can also be offloaded to the standby database in a Data Guard setup.

By using Oracle's cloud automation, these backup and recovery operations are simplified, secure, and follow Oracle best practices. This ensures minimal data loss and high availability of critical data.

---

## **Step-by-Step Breakdown**

---

### **1. Backup Types**

Oracle Base Database Service supports two main backup types:

- **Automatic Backups**  
  These are scheduled by Oracle if enabled during or after database creation  
  Includes full and incremental backups  
  Archive logs are backed up every 30 minutes  

- **On-Demand Backups**  
  Initiated manually by the user  
  Persist until explicitly deleted by the user  

---

### **2. Backup Destinations**

You can choose between two destinations:

- **Recovery Service** (Recommended)  
  Default option with advanced features  
  Offers real-time redo log shipping and faster restore  
  Stores data outside customer tenancy for extra safety  
  Retention period: 90 to 3650 days  
  Backup replication across availability domains  

- **Object Storage**  
  Simpler and traditional method  
  Uses full backup weekly and incremental backup daily  
  Retention period: 7 to 60 days  
  Default is 30 days  

---

### **3. Enabling Automatic Backups**

**During Database Creation:**

- Choose recovery service or object storage as the backup destination  
- Set retention period  
- Choose if real-time data protection is required  
- Schedule full and incremental backups  
- Optionally, take the first backup immediately  

**For Existing Databases:**

- Go to Database Details page  
- Click Configure Automatic Backups  
- Enable backups and configure destination and schedule  

---

### **4. Creating On-Demand Backup**

- Navigate to the Database Details page  
- Under Resources, click Backups  
- Click Create Backup  
- Provide a name and confirm  
- The backup will appear in the list with status Creating and then Active when completed  
- These backups stay until deleted manually  

---

### **5. Viewing Backup History**

- Go to Database Details page  
- Under Resources, click Backups  
- All automatic and on-demand backups are listed  
- Each backup shows its type, timestamp, and status  

---

### **6. Restoring a Database**

From the Database Details page, click Restore. You will be given three options:

- **Restore to Latest**  
  Restores to the most recent consistent state  

- **Restore to Timestamp**  
  Specify a date and time to recover to  

- **Restore to System Change Number (SCN)**  
  Use SCN from logs or queries to perform precise recovery  

Click Restore Database to begin the operation. The system handles recovery through RMAN automatically.

---

### **7. Backup and Restore from Standby Database**

If you have Data Guard configured, you can offload backup tasks to the standby database to reduce load on the primary.

- Enable automatic backups on the standby  
- Schedule retention and backup times like the primary  
- You can restore a database from backups taken on standby  
- Backup location must match between primary and standby  
- Recovery service supports restoration from either standby or primary backups  
- Object storage only supports restore from its own backups  

---

### **8. Retention and Deletion Settings**

- You can specify whether to keep backups after database termination  
  - Options: keep as per retention period or retain for 72 hours  
- Recovery service supports long-term retention up to 10 years  
- All backups are encrypted by default  

---

### **9. Summary Table**

| Feature | Description |
|--------|-------------|
| Automatic Backups | Scheduled by Oracle, includes archive logs |
| On-Demand Backups | User-initiated, must be manually deleted |
| Recovery Service | Faster, more secure, immutable backups |
| Object Storage | Traditional, simpler backup system |
| Real-Time Data Protection | Zero data loss with redo log shipping |
| Retention Periods | 30 to 60 days for object storage, 90 to 3650 days for recovery service |
| Restore Options | Latest state, timestamp, or SCN |
| Data Guard Integration | Offload backups to standby, restore from either node |

---

### **End of Lesson**

By following this guide, you can:

- Understand all backup options  
- Enable and manage backups through the OCI console  
- Perform restores based on business need  
- Offload backup tasks to the standby database  
- Ensure high availability and minimal data loss in case of failure

---

