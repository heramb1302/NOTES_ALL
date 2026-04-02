

![[Pasted image 20260402135646.png]]


### What is an AMI?

An **Amazon Machine Image (AMI)** acts as a master template that contains all the essential information and configurations required to launch a virtual server (an EC2 instance) in AWS.

### Key Components of an AMI

According to the slide, an AMI includes four primary details:

- **Operating System:** The base software that will run on the instance (e.g., Ubuntu, Amazon Linux, Windows).
    
- **Architecture:** The underlying hardware design it supports (e.g., 32-bit, 64-bit, x86, ARM).
    
- **Storage for the root device:** Where the OS is actually installed. This can be:
    
    - _Instance Store:_ Temporary, ephemeral storage directly attached to the host hardware.
        
    - _EBS-backed (Elastic Block Store):_ Persistent, network-attached storage (the most common choice).
        
- **Virtualization Type:** How the instance interacts with the underlying hardware:
    
    - _HVM (Hardware Virtual Machine):_ Allows the guest OS to run as if it's on bare metal, providing better performance.
        
    - _PV (Paravirtual):_ An older type where the guest OS knows it is virtualized.
        

### Understanding the Diagram

The diagram on the right visually explains how an AMI translates into running instances:

1. **Server (Bottom):** This represents the physical hardware sitting in an AWS data center.
    
2. **Xen Hypervisor (Middle):** This is the virtualization software layer running on the physical server. It uses the "ISO" (representing the OS image/AMI template) to allocate resources and create isolated environments.
    
3. **Instances (Top):** Using that single blueprint (the AMI), the hypervisor can spin up multiple, identical virtual machines (the orange boxes) on that underlying physical server.
    

**Analogy:** You can think of an AMI as a "cookie cutter" and the EC2 instances as the "cookies." You only need one cookie cutter to stamp out as many identical cookies as you need.

![[Pasted image 20260402135732.png]]


Based on the slide provided, here are the core concepts regarding how you can customize and distribute Amazon Machine Images (AMIs).

This slide breaks down into two distinct, very useful workflows:

### 1. Creating a Custom AMI (The "Golden Image")

The top half of the diagram illustrates the process of "baking" your own custom AMI.

Instead of launching a completely blank server every time, you can:

1. **Start with a Base:** Take a standard OS like Amazon Linux.
    
2. **Install Software:** Log into that instance and install all your required dependencies. The slide uses Python, Ruby, Apache, and the AWS CLI as examples. For your own projects, this is exactly where you would pre-install your Java environment for Spring Boot or your Python setup for Django.
    
3. **Create the Image:** Once everything is configured perfectly, you capture that exact state and save it as your own custom AMI.
    
4. **Launch Instances:** Now, you can use that single custom AMI to launch dozens of new EC2 instances. They will boot up in seconds with all your software already installed and ready to go, skipping the manual setup process entirely.
    

### 2. Copying an AMI Across Regions

The bottom half of the diagram addresses a crucial rule in AWS: **AMIs are locked to the Region they are created in.**

- If you create an AMI in **`us-east-1`** (N. Virginia), you cannot simply launch an EC2 instance from it in another region.
    
- To deploy your application globally, or to move it closer to your users to reduce latency—such as moving it to the **`ap-south-1`** (Mumbai) region—you must explicitly use the **Copy AMI** function.
    
- AWS will securely transfer the underlying snapshot data to the new region, creating a new, independent AMI there that you can use to launch local instances.
    

Essentially, the top process saves you from doing repetitive software installations, and the bottom process allows you to distribute that perfectly configured server anywhere in the world.


![[Pasted image 20260402135903.png]]



Based on the slide provided, here are the key notes explaining the difference between standard Public IPs and Elastic IPs in AWS.

This is a crucial concept when you start making your applications accessible to the outside world.

### Standard Public IP (The Default)

When you launch an EC2 instance, AWS can automatically assign it a Public IP so it can communicate with the internet.

- **Temporary Nature:** The most important detail is that this IP is **dynamic**. If you stop and restart your EC2 instance, that IP address goes back into the AWS pool, and your instance is given a completely new, random IP address.
    
- **Account Association:** It isn't permanently tied to your AWS account; you are just borrowing it from AWS while the server is running.
    
- **Pricing Update (Important Correction to the Slide):** The slide mentions there are no charges for standard Public IPs. However, **AWS changed their pricing policy in February 2024**. Due to the global shortage of IPv4 addresses, AWS now charges a small hourly fee for _all_ public IPv4 addresses, whether standard or Elastic.
    

### Elastic IP (The Static Option)

An Elastic IP (EIP) is AWS's term for a **static public IP address**.

- **Permanent Nature:** Once you allocate an Elastic IP, it remains exactly the same. If you stop, restart, or even terminate the underlying EC2 instance, the Elastic IP address doesn't change.
    
- **Account Association:** It is reserved specifically for _your_ AWS account until you manually click "Release."
    
- **Pricing Quirk:** To prevent people from hoarding scarce static IPs, AWS historically only charged you for an Elastic IP if it was **not** attached to a running server. (Though again, note the recent 2024 pricing change where all public IPs now incur a baseline cost).
    

### Why does this matter for your projects?

Imagine you are deploying a **Spring Boot API** or a **Django web application** on an EC2 instance.

You buy a domain name (like `www.mycoolapp.com`) and configure the DNS settings to point to your server's IP address.

- If you use a **Standard Public IP** and your server crashes or needs a reboot for a security patch, it will come back online with a _new_ IP. Your domain name will still be pointing to the old IP, and your website will go down until you manually update your DNS records (which can take hours to propagate).
    
- If you use an **Elastic IP**, you can safely reboot the server. It boots back up, attaches to the exact same Elastic IP, and your domain name continues working seamlessly without any DNS changes.