# Assignment II: Database Creation, Deletion & OEM

**name:** ingabire bienvenu
**Student ID:** 26117
**Course:** Database Development with PL/SQL (INSY 8311)  


## 🧩 Task 1: Create a New Pluggable Database (PDB) 

**PDB Name:** `ib_pdb_26117`  
**User:** `ingabire_plsqlauca_26117`  
**Password:** `kenny` 

###Screenshoot1
<img width="1920" height="1080" alt="Screenshot (345)" src="https://github.com/user-attachments/assets/6136ab48-6949-43a3-a65a-ba69f780be8c" />

### Screenshots2
<img width="1920" height="1080" alt="Screenshot (346)" src="https://github.com/user-attachments/assets/75e579fb-aa56-40ec-9e57-a31a6ea71596" />

Task 2: Create and Delete a PDB 

PDB Name: in_to_delete_pdb_26117
User: ingabire_delete_26117

<img width="1920" height="1080" alt="Screenshot (347)" src="https://github.com/user-attachments/assets/1ff0dde3-9bbf-418a-a4a5-14bb7a675cf5" />

<img width="1920" height="1080" alt="Screenshot (348)" src="https://github.com/user-attachments/assets/ab8af8bb-e213-4981-9491-59c9400184f6" />


Task 3: Oracle Enterprise Manager (OEM) 
Configuration Steps
Always show details
EXEC DBMS_XDB_CONFIG.SETHTTPPORT(8080);
EXEC DBMS_XDB_CONFIG.SETHTTPSPORT(5500);

SELECT DBMS_XDB_CONFIG.GETHTTPPORT() AS HTTP_PORT, 
       DBMS_XDB_CONFIG.GETHTTPSPORT() AS HTTPS_PORT 
FROM DUAL;

Access Path: (https://localhost:5500/em/shell)
Login Credentials: 
username = SYS
Password = kenny
Container Name  =	CDB$ROOT
Role = SYSDBA


<img width="1920" height="1080" alt="Screenshot (349)" src="https://github.com/user-attachments/assets/39c542d6-234f-4d5e-a268-d1eb94ac4923" />

<img width="1920" height="1080" alt="Screenshot (350)" src="https://github.com/user-attachments/assets/18d56dc8-2b9c-43cd-a210-925b92490ba5" />

###  Issues Encountered & Solutions

## Issue 1: File Path Error During PDB Creation

**Cause:**  
Incorrect syntax or invalid path when using `FILE_NAME_CONVERT` to create a new Pluggable Database.

**Resolution:**
- Replaced `FILE_NAME_CONVERT` with the more reliable `CREATE_FILE_DEST` parameter:
  ```sql
  CREATE PLUGGABLE DATABASE in_pdb_26117
  ADMIN USER ingabire_delete_26117 IDENTIFIED BY kenny
  CREATE_FILE_DEST = 'D:\ORACLE21CHOME\ORADATA\ORCL\ingabire_plsqlauca_26117';

##  Issue 2: Oracle Installation Errors

### Problem 1 — Listener Configuration Failure


**📍 Cause**  
The **Oracle Listener service** wasn’t started during installation or was misconfigured.

**✅ Resolution**
1. Opened **Command Prompt as Administrator**.  
2. Started the listener manually:
   ```bash
   lsnrctl start
ORA-12514: TNS: listener does not currently know of service requested
The Oracle service (OracleServiceXE) didn’t start after system reboot.
I started the service manually to Verified it via Windows Services → OracleServiceXE → Status: Running = net start OracleServiceXE
Result: Database service started successfully, and connection via SQL*Plus worked again.















