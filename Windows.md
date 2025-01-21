### **1. Local Users**

Local users are accounts created and managed on a specific computer. They exist independently on each machine and have no access to network-wide resources unless explicitly configured.

#### **Characteristics of Local Users**:

- **Scope**: Can only access the local computer where the account is created.
- **Management**: Created and managed through the local operating system settings or tools (e.g., **Control Panel** in Windows or `useradd` in Linux).
- **Authentication**: Username and password are stored locally on the computer.
- **Resource Access**: Local users can only access local resources (files, printers, applications) unless network permissions are granted.
- **Offline Access**: Always available on the specific machine, even without a network connection.

#### **Examples of Local Users**:

- Default accounts like `Administrator` (Windows) or `root` (Linux).
- Personal accounts created by individual users for standalone systems.

#### **Use Cases for Local Users**:

- Standalone systems not connected to a network.
- Testing or development environments.
- Basic user accounts on personal computers.

---

### **2. Domain Users**

Domain users are accounts managed by a centralized domain controller in a networked environment, typically under a directory service like **Active Directory (AD)** in Windows.

#### **Characteristics of Domain Users**:

- **Scope**: Can log in to any machine that is part of the domain (if permissions allow).
- **Management**: Created and managed on the domain controller, not individual machines.
- **Authentication**: Username and password are authenticated by the domain controller.
- **Resource Access**: Can access shared network resources (printers, files, applications) based on domain permissions.
- **Centralized Policies**: Managed using **Group Policies** for consistent security and configuration settings across all domain-connected machines.
- **Offline Access**: May have cached credentials for offline logins on previously accessed machines.

#### **Examples of Domain Users**:

- Corporate accounts managed by IT (e.g., `jdoe@company.com`).
- Role-based accounts for accessing shared network resources.

#### **Use Cases for Domain Users**:

- Large organizations with multiple users and computers.
- Centralized management of user access and policies.
- Networks requiring secure, scalable user authentication and resource access.

---

### **Comparison of Local Users and Domain Users**

|Feature|Local Users|Domain Users|
|---|---|---|
|**Scope**|Single computer|Entire domain network|
|**Authentication**|Local computer only|Centralized via domain controller|
|**Resource Access**|Limited to the local machine|Network-wide resource access|
|**Management**|Local settings|Domain controller|
|**Offline Availability**|Always available|Available if credentials are cached|
|**Use Case**|Standalone systems|Managed enterprise environments|

---

### **Hybrid Use**:

- In many environments, a system may have both **local users** and **domain users**. For example:
    - IT administrators might use a **local admin account** for emergency troubleshooting.
    - Regular employees use **domain accounts** to access network resources.

---

### **Key Tools for Managing Users**:

- **Windows**:
    - Local Users: **Control Panel > User Accounts**, `Computer Management` > Local Users and Groups.
    - Domain Users: **Active Directory Users and Computers (ADUC)**.
- **Linux**:
    - Local Users: Command-line tools like `useradd`, `passwd`, or `adduser`.
    - Domain Users: Integration with **LDAP**, **Kerberos**, or **Active Directory** (via Samba/Winbind).

---

### **Conclusion**

Local users are best for standalone or single-user systems, while domain users excel in enterprise environments requiring centralized management, scalability, and network resource sharing. Understanding the scope and management of each is critical for effective user and resource administration.

---

# **Event Logs in Windows: Overview**

**Event Logs** are records of significant system, security, and application-related events on a Windows computer. They are crucial for troubleshooting, monitoring, and auditing the behavior of the system and applications.

---

### **Types of Event Logs**

1. **System Log**:
    
    - Contains events related to the operating system and its components.
    - Examples: Driver errors, hardware failures, and system shutdown/startup.
2. **Application Log**:
    
    - Stores events logged by applications or programs.
    - Examples: Application crashes, service-specific errors.
3. **Security Log**:
    
    - Records events related to security, such as login attempts, account management, and audit policies.
    - Examples: Successful/failed login attempts, privilege changes.
    - **Note**: Security logs are governed by audit policies.
4. **Setup Log**:
    
    - Tracks events during Windows installation or setup.
    - Useful for diagnosing installation-related issues.
5. **Forwarded Events**:
    
    - Collects events forwarded from other computers, useful in centralized monitoring setups.

---

### **Accessing Event Logs**

1. **Using Event Viewer**:
    
    - Press `Win + R`, type `eventvwr`, and press Enter.
    - Navigate the logs:
        - **Windows Logs**: System, Application, Security, Setup, and Forwarded Events.
        - **Applications and Services Logs**: Logs specific to applications and services.
    - Use the middle pane to view detailed event information.
2. **Using Command Line or PowerShell**:
    
    - **Command Prompt**:
        
        bash
        
        Copy code
        
        `wevtutil qe System`
        
        This queries the system log.
    - **PowerShell**:
        
        powershell
        
        Copy code
        
        `Get-EventLog -LogName System`
        
        View specific logs.

---

### **Event Log Structure**

Each event log entry includes:

- **Date/Time**: When the event occurred.
- **Event ID**: A unique identifier for the event type.
- **Source**: The application or system component generating the event.
- **Level**: Severity level (e.g., Information, Warning, Error, Critical).
- **User**: The user account under which the event occurred.
- **Description**: Detailed information about the event.

---

### **Common Event IDs**

|**Event ID**|**Log**|**Description**|
|---|---|---|
|4624|Security|Successful logon.|
|4625|Security|Failed logon attempt.|
|6008|System|Unexpected shutdown.|
|1000|Application|Application crash or error.|
|41|System|Kernel power issue, typically caused by a crash.|

---

### **Managing Event Logs**

1. **Filter Events**:
    
    - In Event Viewer, use the **Filter Current Log** option to narrow down results by Event ID, severity, source, etc.
2. **Export Logs**:
    
    - Right-click a log (e.g., System) and select **Save All Events As** to export logs as `.evtx`, `.txt`, or `.xml`.
3. **Clear Logs**:
    
    - To clear old logs, right-click a log (e.g., Application) and choose **Clear Log**.
4. **Enable/Disable Logging**:
    
    - Use **Group Policy** or **Audit Policies** to enable or disable specific types of logging, especially for security logs.

---

### **Use Cases for Event Logs**

- **Troubleshooting**: Diagnose application or system errors.
- **Security Monitoring**: Identify unauthorized access attempts or malicious activity.
- **Compliance**: Ensure adherence to regulatory requirements by auditing events.
- **Performance Monitoring**: Detect resource bottlenecks and optimize performance.

---

### **Conclusion**

Event logs are an invaluable tool for managing and securing Windows systems. By understanding the types of logs and how to analyze them, administrators and users can maintain the health, security, and efficiency of their systems.

---

# **Basic Windows 10 Command-Line Commands**

Here’s a list of commonly used commands in Windows 10's Command Prompt (CMD) with their purpose:

---

### **1. Navigation Commands**

- `dir`
    
    - Lists files and directories in the current directory.
    - Example: `dir /p` (pauses output).
- `cd` or `chdir`
    
    - Changes the current directory.
    - Example: `cd C:\Users\YourName\Documents`.
- `cd ..`
    
    - Moves to the parent directory.
- `cls`
    
    - Clears the screen.
- `tree`
    
    - Displays the directory structure of a drive or path in a tree format.
    - Example: `tree C:\`.

---

### **2. File and Directory Management**

- `mkdir` or `md`
    
    - Creates a new directory.
    - Example: `mkdir NewFolder`.
- `rmdir`
    
    - Removes a directory (must be empty).
    - Example: `rmdir OldFolder`.
- `del`
    
    - Deletes files.
    - Example: `del example.txt`.
- `copy`
    
    - Copies files from one location to another.
    - Example: `copy file.txt D:\Backup`.
- `move`
    
    - Moves or renames files.
    - Example: `move file.txt D:\Folder`.
- `ren` or `rename`
    
    - Renames a file or directory.
    - Example: `rename oldfile.txt newfile.txt`.

---

### **3. System Information and Diagnostics**

- `ipconfig`
    
    - Displays network configuration details.
    - Example: `ipconfig /all` (shows detailed network info).
- `ping`
    
    - Tests network connectivity to a specified address.
    - Example: `ping www.google.com`.
- `systeminfo`
    
    - Displays detailed information about the system.
- `tasklist`
    
    - Lists all running processes.
    - Example: `tasklist | find "notepad.exe"` (checks if Notepad is running).
- `taskkill`
    
    - Ends a running process.
    - Example: `taskkill /IM notepad.exe /F`.
- `shutdown`
    
    - Shuts down or restarts the computer.
    - Example: `shutdown /r` (restart).

---

### **4. Disk and Storage Management**

- `chkdsk`
    
    - Checks the disk for errors and attempts to repair them.
    - Example: `chkdsk C: /f /r`.
- `diskpart`
    
    - Opens the disk partitioning tool (use cautiously).
    - Example: `diskpart`.
- `format`
    
    - Formats a specified drive.
    - Example: `format D:`.

---

### **5. File Searching**

- `find`
    
    - Searches for text in files.
    - Example: `find "error" logfile.txt`.
- `where`
    
    - Locates the path of a file or command.
    - Example: `where notepad`.

---

### **6. User and Permissions Management**

- `net user`
    
    - Displays user accounts or manages them.
    - Example: `net user` (lists users), `net user username /add` (adds a user).
- `netstat`
    
    - Displays active network connections.
    - Example: `netstat -an`.
- `whoami`
    
    - Displays the currently logged-in user.

---

### **7. Utility Commands**

- `echo`
    
    - Displays messages or enables/disables command echoing.
    - Example: `echo Hello, World!`.
- `type`
    
    - Displays the contents of a file.
    - Example: `type file.txt`.
- `fc`
    
    - Compares two files and shows the differences.
    - Example: `fc file1.txt file2.txt`.
- `set`
    
    - Displays, sets, or removes environment variables.
    - Example: `set PATH`.
- `help`
    
    - Provides a list of available commands or details about a specific command.
    - Example: `help dir`.

---

### **8. Advanced Commands**

- `sfc`
    
    - Scans and repairs system files.
    - Example: `sfc /scannow`.
- `powershell`
    
    - Launches Windows PowerShell from Command Prompt.
- `reg`
    
    - Manages the Windows Registry.
    - Example: `reg query HKLM\Software`.
- `wmic`
    
    - Windows Management Instrumentation Command-line tool for system management.
    - Example: `wmic process list`.

---

### **9. Shortcuts and Tips**

- Use `Ctrl + C` to stop a running command.
- Use `Tab` for auto-completion of file or directory names.
- Use `>` to redirect output to a file.
    - Example: `dir > output.txt` (saves directory listing to `output.txt`).

---

These commands cover the essentials for navigating, managing files, diagnosing system issues, and handling basic administrative tasks in Windows 10.