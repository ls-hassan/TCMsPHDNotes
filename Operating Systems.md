![[Pasted image 20250115172257.png]]

An **Operating System (OS)** is software that manages hardware resources and provides services for applications. It acts as an intermediary between users, applications, and hardware, ensuring that resources are used efficiently and processes are executed correctly.

---

### **Key Functions of an Operating System**

1. **Abstraction:**
    
    - The OS abstracts complex hardware details and provides a simplified interface for users and applications.
    - For example, rather than requiring programs to handle individual hardware instructions, the OS provides standardized APIs and abstractions for hardware resources like memory, storage, and input/output.
2. **Arbitration:**
    
    - The OS arbitrates access to hardware resources among multiple users and processes to avoid conflicts and ensure fairness.
    - Examples include CPU scheduling, memory allocation, and disk I/O management.

---

### **OS Architecture: Userland vs Kernel**

The OS is split into **two main areas**: the **userland (user space)** and the **kernel (kernel space)**.

#### **1. Userland (User Space)**

- **Description:**
    
    - The userland is where **applications** and **processes** run.
    - It is separate from the kernel to provide security and stability (user processes can't directly access hardware).
    - Applications in userland rely on system calls to interact with the kernel.
- **Examples of Userland Tasks:**
    
    - Running applications (e.g., web browsers, text editors).
    - Accessing system resources via APIs (e.g., file systems, network).
    - Interfacing with the shell (CLI) or GUI.
- **Abstraction in Userland:**
    
    - Applications don't directly manipulate hardware; they use the OS-provided **Application Programming Interface (API)** to perform actions like reading files, sending data over a network, or rendering graphics.

---

#### **2. Kernel (Kernel Space)**

- **Description:**
    
    - The kernel is the **core of the OS** and operates at the lowest level.
    - It manages **hardware resources** (CPU, memory, I/O devices) and provides services to userland applications through system calls.
    - Runs with **full access to hardware** (privileged mode).
- **Key Functions of the Kernel:**
    
    - **Process Management:** Scheduling, creation, and termination of processes.
    - **Memory Management:** Allocation and protection of memory for processes.
    - **Device Drivers:** Interfaces between the OS and hardware devices.
    - **File System Management:** Providing access to data stored on storage devices.
    - **Security and Protection:** Preventing unauthorized access to resources.
- **Arbitration in the Kernel:**
    
    - The kernel decides which process gets CPU time, how memory is allocated, and when to perform I/O operations to ensure system stability and performance.

---

### **API Calls and System Calls**

#### **1. API (Application Programming Interface):**

- **Description:**
    
    - An API is a set of programming interfaces provided by the OS or libraries that applications use to interact with the system.
    - It provides **abstraction** by allowing applications to perform tasks (e.g., opening files, accessing networks) without needing to know how the hardware works.
- **Example APIs:**
    
    - **Windows API:** Used by Windows applications to interact with the OS.
    - **POSIX API:** A standardized API for Unix-like operating systems (Linux, macOS).
- **Use in Userland:**
    
    - An application calls the OS API (e.g., `read()`, `write()`, `socket()`), which internally triggers system calls to the kernel.

---

#### **2. System Calls:**

- **Description:**
    
    - System calls are the mechanism for userland processes to request services from the kernel.
    - They act as a bridge between userland and kernel space.
- **Examples of System Calls:**
    
    - **Process Management:** `fork()`, `exec()`, `wait()`.
    - **File Operations:** `open()`, `read()`, `write()`, `close()`.
    - **Memory Management:** `mmap()`, `brk()`.
    - **Networking:** `socket()`, `bind()`, `send()`, `recv()`.
- **Process:**
    
    1. The application makes an **API call** (e.g., `fopen()` in C).
    2. The API internally uses a **system call** (e.g., `open()`).
    3. The system call transitions the process from **user mode** to **kernel mode**.
    4. The kernel executes the requested task and returns the result.

---

### **Relationship Between Applications, OS, and Hardware**

The OS provides layers of abstraction and control between **applications** and **hardware**:

1. **Applications (Userland):**
    
    - Applications like web browsers, games, and text editors run in userland.
    - They communicate with the OS via APIs.
    - Applications are unaware of the hardware specifics, relying on the OS for access.
2. **OS (Userland + Kernel):**
    
    - Provides an interface for applications and manages hardware resources.
    - Ensures arbitration so multiple processes can share hardware resources fairly and efficiently.
    - Offers abstractions to hide the complexity of hardware.
3. **Hardware:**
    
    - Includes the CPU, memory, storage, I/O devices, and network interfaces.
    - Hardware executes the instructions sent by the OS but cannot be directly accessed by userland applications.

### **Example: Opening a File**

Let’s walk through the process of an application opening a file:

1. **Application in Userland:**
    
    - A text editor calls an API function like `fopen("example.txt", "r")`.
2. **API Call:**
    
    - The API converts the request into a system call (e.g., `open()`).
3. **System Call:**
    
    - The `open()` system call is sent to the kernel, transitioning the process from userland to kernel space.
4. **Kernel:**
    
    - The kernel interacts with the file system and hardware (e.g., disk controller) to retrieve the file.
5. **Return to Userland:**
    
    - The kernel returns the file descriptor or an error code to the application via the API.
6. **Application Uses the File:**
    
    - The application uses the file descriptor to read or write data, which may involve additional system calls like `read()` or `write()`.

---

### **Key Points to Remember**

- **Abstraction:** The OS simplifies hardware complexity for applications through APIs and system calls.
- **Arbitration:** The OS ensures fair and efficient resource usage among competing processes.
- **Userland vs Kernel:**
    - Userland is where applications run and make API calls.
    - The kernel manages hardware resources and handles system calls.
- **APIs:** Provide a user-friendly interface for applications to perform complex tasks.
- **Hardware Access:** Applications don’t directly interact with hardware; they rely on the OS for this.

---
# File system

### **1. What is a File System?**

- A **file system** is a method used by operating systems to store, organize, and retrieve data on storage devices like hard drives, SSDs, or USB drives.
- It provides a structured way to manage files and directories.

---

### **2. Common File Systems**

- **NTFS (Windows):** Used in modern Windows systems, supports large files, encryption, and permissions.
- **FAT32 (Windows, macOS, Linux):** Older, widely compatible, but limited to 4GB file size.
- **ext4 (Linux):** Default file system for Linux, supports journaling and large volumes.
- **APFS (macOS):** Optimized for SSDs, used by macOS.
- **HFS+ (macOS):** Predecessor to APFS.

---

### **3. File System Hierarchy**

- Files and folders (directories) are organized in a hierarchical structure:
    - **Root Directory (`/` or `C:\`)**: The topmost directory in the file system.
    - **Subdirectories:** Folders nested within other folders.
    - **Files:** Data stored inside directories.

---

### **4. Navigation Basics**

#### **a. File Paths**

- **Absolute Path:** Specifies the full path from the root directory.
    - Example: `/home/user/documents/file.txt` (Linux/Mac), `C:\Users\User\Documents\file.txt` (Windows).
- **Relative Path:** Specifies the path relative to the current directory.
    - Example: `documents/file.txt`.

---

#### **b. Basic Commands**

- **Windows Command Prompt:**
    
    - `dir`: Lists files and directories in the current folder.
    - `cd [folder]`: Change directory to the specified folder.
    - `cd ..`: Move up one directory level.
    - `mkdir [folder]`: Create a new folder.
    - `del [file]`: Delete a file.
    - `rmdir [folder]`: Remove an empty folder.
- **Linux/macOS Terminal:**
    
    - `ls`: Lists files and directories in the current folder.
    - `cd [folder]`: Change directory to the specified folder.
    - `cd ..`: Move up one directory level.
    - `mkdir [folder]`: Create a new folder.
    - `rm [file]`: Delete a file.
    - `rmdir [folder]`: Remove an empty folder.

---

#### **c. Navigation Shortcuts**

- **`.` (dot):** Refers to the current directory.
- **`..` (double dot):** Refers to the parent directory.
- **`~` (tilde):** Refers to the home directory of the current user.
- **`/` (Linux/Mac) or `\` (Windows):** Separates directories in paths.

---

### **5. Common File Types**

- **Text Files:** `.txt`, `.md`.
- **Executable Files:** `.exe` (Windows), `.sh` (Linux/macOS).
- **Image Files:** `.jpg`, `.png`.
- **Compressed Files:** `.zip`, `.tar.gz`.

---

### **6. File Permissions (Linux/Mac)**

- **Read (r), Write (w), Execute (x):** Permissions for files and directories.
- **User/Group/Others:** Permissions are assigned to the owner, group, and everyone else.
- Use `ls -l` to view permissions and `chmod` to modify them.


