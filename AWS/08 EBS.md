### **What is EBS?**

**EBS (Elastic Block Storage)** is a block-level storage service provided by Amazon.

**Core Characteristics & Constraints:**

- **EC2 Integration:** It is designed to be used exclusively with separate Amazon EC2 instances.
    
- **1:1 Attachment Rule:** No two EC2 instances can have the _same_ EBS volume attached to them simultaneously.
    
- **Performance:** Because the storage is directly attached to the instance, it provides a high-performance option for many use cases.
    

**Common Use Cases:**

- Hosting various databases (both relational and non-relational).
    
- Software testing and development environments.
    
- A wide range of general applications requiring block storage.

### **Features of EBS (and related EC2 concepts)**

- **Persistent Storage:** Amazon Elastic Block Store (Amazon EBS) provides persistent storage volumes, commonly referred to simply as Amazon EBS volumes. Unlike instance store volumes, data on an EBS volume persists independently of the life of the instance.
    
- **Physical Location:** EBS volumes and EC2 instances are tied to specific physical locations. These locations are categorized into **Regions** (broad geographic areas) and **Availability Zones** (isolated locations within those regions).
    
- **Network Security (Security Groups):** You use security groups to act as a virtual firewall. They allow you to specify the exact protocols, ports, and source IP ranges that are allowed to reach your instances (and therefore interact with the data on your attached EBS volumes).
    
- **Static Addressing (Elastic IP):** Elastic IP addresses are static IPv4 addresses designed for dynamic cloud computing. They allow you to mask instance or software failures by rapidly remapping the address to another instance in your account.

### **Introduction to EBS: File System Basics**

Before diving into block storage specifically, this slide illustrates how operating systems typically organize storage.

**Key Concepts:**

- **Physical vs. Logical Volumes:** A single, actual hardware drive (**Physical Volume**) can be partitioned or divided into multiple independent, virtual drives known as **Logical Volumes**. In the diagram, the physical hard drive is split into logical drives labeled `C:` and `D:` (a common Windows convention).
    
- **Hierarchical Structure:** Within each logical volume, data is organized in a top-down tree structure.
    
- **Directories and Files:** * **Directories (Folders):** Used to group and organize data. They can contain files or other sub-directories.
    
    - **Files:** The actual data or documents stored within those directories.




| **Feature**       | **Amazon EBS (Elastic Block Store)**                                              | **Amazon S3 (Simple Storage Service)**                                                        |
| ----------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| **Storage Type**  | **Block Storage:** Best for frequently changing data.                             | **Object Storage:** Best for static files and "write once, read many" data.                   |
| **Analogy**       | A local hard drive or SSD plugged into your computer.                             | A giant, infinite "bucket" or Dropbox for your files.                                         |
| **Accessibility** | Tied to a specific **EC2 instance**. Only one instance can write to it at a time. | Accessible from **anywhere** via a URL or API.                                                |
| **Performance**   | **Very Low Latency.** Essential for databases and boot volumes.                   | **High Throughput**, but higher latency than EBS.                                             |
| **Scalability**   | Fixed size (e.g., 100GB). You must manually increase it.                          | **Virtually Infinite.** It scales automatically as you add more data.                         |
| **Durability**    | Data is replicated within a single Availability Zone.                             | Data is automatically replicated across multiple geographic zones (99.999999999% durability). |


### **EBS Characteristics & Performance Metrics**

**Core Nature of EBS:**

- **Raw Storage:** EBS provides raw, unformatted block-level storage. When you attach it to an EC2 instance, it appears as a raw, unformatted external drive that you must format with a file system (like ext4 or NTFS) before using.
    
- **Independent Lifecycle:** An EBS volume's data persists independently from the life of the EC2 instance it is attached to. If the instance is stopped or terminated, the data on the EBS volume remains safe.
    
- **High Availability (Replication):** To protect against hardware failure, an EBS volume is automatically replicated across multiple servers within its specific **Availability Zone (AZ)**.
    

**Key Performance Measurements:** Understanding the difference between these two metrics is crucial for choosing the right EBS volume type for your workload:

- **Throughput (Sequential):** * This measures the _amount_ of data transferred over time (e.g., Megabytes per second or MB/s).
    
    - It represents the sequential transfer rate that a drive (SSD or HDD) can maintain continuously.
        
    - _Best for:_ Large, continuous files like streaming video, big data processing, or log processing.
        
- **IOPS (Random):**
    
    - Input/Output Operations Per Second.
        
    - This measures the _number_ of read/write operations a drive can handle per second, specifically when data is being read from or written to **RANDOM** locations on the disk.
        
    - _Best for:_ Transactional workloads like relational databases (MySQL, PostgreSQL) or NoSQL databases where small bits of data are scattered everywhere and need to be accessed quickly.

![[Pasted image 20260403122235.png]]

### **EBS Multi-Attach Feature**

This slide introduces an exception to the standard "1:1 attachment rule" mentioned earlier, highlighting a specific feature called **EBS Multi-Attach**.

**The Problem: Without Multi-Attach**

- Historically, if you had multiple EC2 instances that all needed access to the exact same data (e.g., a massive machine learning training dataset), you had to provision separate EBS volumes for _each_ instance.
    
- You then had to copy the dataset onto every single volume. This resulted in wasted storage space, increased costs, and overhead in managing multiple copies of the data.
    

**The Solution: With Multi-Attach**

- The Multi-Attach feature allows you to attach a **single** EBS volume to **multiple** EC2 instances concurrently (up to 16 instances within the same Availability Zone).
    
- **Key Benefit shown in diagram:** As the diagram illustrates, you can have a "Single EBS Volume for training datasets." All the EC2 instances can read from this one central volume simultaneously.
    
- This dramatically simplifies storage management, reduces storage costs (by eliminating duplicate copies), and makes it easier to scale out applications that require shared access to a specific block of data.


![[Pasted image 20260403122402.png]]


### **EBS Snapshot Copying**

This slide explains how you can move EBS data across different AWS geographical locations (Regions) using snapshots.

**1. Cross-Region Copying Workflow** The primary diagram illustrates the step-by-step process of migrating a volume from one region (e.g., `us-east-1`) to another (e.g., `us-west-2`):

- **Step 1 (Snapshot):** You create a backup (Snapshot) of your existing EBS volume in the original region (`us-east-1`).
    
- **Step 2 (Copy):** You initiate a copy of that snapshot, specifying the destination region (`us-west-2`). AWS securely transfers the data.
    
- **Step 3 (Create):** In the new region (`us-west-2`), you use the copied snapshot to create a brand new EBS volume.
    
- **Step 4 (Attach):** Finally, you can attach this new volume to an EC2 instance running in that new region.
    

_Use Cases:_ This process is essential for Disaster Recovery (having backups in a different geographic location) and for migrating applications closer to new user bases.

**2. Encryption During Copying** The second point highlights a crucial security feature: **Encrypt during copying**.

- If your original EBS volume (and its snapshot) was unencrypted, you have the option to apply encryption _during_ the copy process.
    
- The resulting copied snapshot in the new region will be encrypted, and any volumes created from it will also be encrypted, providing an easy way to secure previously unencrypted data.

