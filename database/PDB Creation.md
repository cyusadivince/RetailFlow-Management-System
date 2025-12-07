# 📘 **Pluggable Database Creation Document**

### *Oracle 21c XE — PDB: `Monday_27516_Divince_Retail_flow_DB`*

This document describes the process used to create the Oracle 21c XE pluggable database **Monday_27516_Divince_Retail_flow_DB**, including the creation of its admin user and file storage configuration.

---

## 🗄️ **1. Overview**

A new Oracle **Pluggable Database (PDB)** named:

```
Monday_27516_Divince_Retail_flow_DB
```

was created using the `CREATE PLUGGABLE DATABASE` SQL command.
This PDB is configured with a custom admin user and uses a local file system location for database storage.

---

## 👤 **2. Admin User**

The PDB includes a local administrative user:

| Parameter    | Value     |
| ------------ | --------- |
| **Username** | `cyusa`   |
| **Password** | `divince` |
| **Role**     | PDB Admin |

This user has all privileges required to administer and manage pluggable database operations.

---

## 📂 **3. File Location Mapping**

Oracle requires a **FILE_NAME_CONVERT** clause when creating a new PDB using the seed (`pdbseed`).
This maps the default seed file path to the custom PDB storage path.

### **Old Path (Seed)**

```
C:\app\CYUSA\product\21c\oradata\XE\pdbseed
```

### **New PDB Path**

```
C:\app\CYUSA\product\21c\oradata\XE\XEPDB1\Monday_27516_Divince_Retail_flow_DB
```

This allows the PDB to be physically stored in a different directory structure under the same Oracle XE environment.

---

## 🧩 **4. Full SQL Command**

```sql
CREATE PLUGGABLE DATABASE Monday_27516_Divince_Retail_flow_DB
    ADMIN USER cyusa IDENTIFIED BY divince
    FILE_NAME_CONVERT = (
        'C:\app\CYUSA\product\21c\oradata\XE\pdbseed',
        'C:\app\CYUSA\product\21c\oradata\XE\XEPDB1\Monday_27516_Divince_Retail_flow_DB'
    );
```

![PDB Creation](https://github.com/cyusadivince/RetailFlow-Management-System/blob/main/ScreenShots/database_objects/pdb_creation.png)
---

## ▶️ **5. Post-Creation Steps**

After creating the PDB, run the following commands:

### **Open the PDB**

```sql
ALTER PLUGGABLE DATABASE Monday_27516_Divince_Retail_flow_DB OPEN;
```

### **Save the State (auto-open on restart)**

```sql
ALTER PLUGGABLE DATABASE Monday_27516_Divince_Retail_flow_DB SAVE STATE;
```

---

## 📝 **6. Verification**

### List all PDBs:

```sql
SHOW PDBS;
```
![Show pdbs](https://github.com/cyusadivince/RetailFlow-Management-System/blob/main/ScreenShots/database_objects/show%20pdb.png)



### Connect to the PDB:

```sql
ALTER SESSION SET CONTAINER = Monday_27516_Divince_Retail_flow_DB;
```

