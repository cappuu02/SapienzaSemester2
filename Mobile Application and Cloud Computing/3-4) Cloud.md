
```ad-abstract
title: Cloud
The name “**_Cloud Computing_**” evokes the cloud as an iconic representation of the Internet (a cloud is often used to represent a network), and computing to indicate the resources required to perform computation, such as storage, CPUs, and memory. 

In simple terms, cloud computing refers to the shift of computing from a single server or data center to an equivalent service accessed via the Internet.

```

# NIST Definition of cloud computing
![[M31.png]]

# Deployment Models

- **Public Cloud**: The cloud is provisioned for open use by the general public
- **Private Cloud**: The cloud infrastructure is provisioned for exclusive use by a single organization.
- **Community Cloud**: The cloud infrastructure is a composition of two or more distinct cloud infrastructures
- **Hybrid Cloud**: The cloud infrastructure is a composition of public and private clouds

```ad-warning
title: PRIVATE CLOUD VS ≠ DATA CENTER
There are many datacenter in the world (see https://www.datacentermap.com/)
- Some of them offers a housing or co-location service
- However, a data center does not necessarily imply a private cloud computing model
- This requires considering how computing resources are managed, as discussed next

```

# Service Models
- IaaS: Infrastructure as a Service 
- PaaS: Platform as a Service
- SaaS: Software as a Service

## Layers
The layered scheme represents the different components of an information system that provides a service. 
- Any layer uses the layer below..
- IaaS Provides the highest flexibility and control. Allows to provision (virtualized) hw (such as servers, networks, ..) very quickly, scale them, shutdown,etc
- PaaS offers a way to develop sw without warrying about any management issue (os updates, patching, )...
- SaaS is a full sw that the providers runs for the user

![[M32.png]]
# THE INITIAL COMPUTING SERVICE FROM AWS
Cloud computing age started in 2006 with Amazon Web Services (AWS)’s Elastic Cloud Computing (EC2) and Simple Storage Systems (S3), plus a Simple Queue Service (SQS)
- `EC2` service allows to use provision size variable VMs
- `S3` is an object storage service (data are stored as objects into beckets), e.g. images, or web site Ensure scalability, data availability, security
- `SQS`, messaging system used to connect other components

![[M33.png]]

# SERVICE FEATURES
![[M34.png]]

## On-Demand Self-Service
The on-demand service feature refers to the ability to consume the computing facility as much as needed at any moment, i.e., through a user-friendly UI or programmatically, e.g. python script, or Infrastructure as Code (IaC) .

The requested cloud services is provisioned in a short period of time and without any need of human intervention at vendor’s end. 

```ad-example
title: Example from AWS
1. Sign in to the management console (aws) 
2. Open EC2 console choosing EC2 under compute 
   ![[M35.png]]
3. Select a AWS Region
   ![[M36.png]]
4. Lunch the instance 
   
![[M37.png]]

- Among other aspects, in the advanced setting is it possible to specify the Tenancy option. 
- ==Shared tenant==: default, means that the VM shares the same HW with other tenants from which it is isolated 
- ==Dedicated Instance==: the instance run on HW only used by the customer
- ==Dedicated Host==:the customer has full visibility of the underlying hardware. In particular, it allows the use of licensed software with hardware-based licensing requirements, by bringing your own licenses (BYOL

```

## Resource Pooling
The provider's computing resources are centrally managed in a pool and shared among all users.

Although not explicitly mentioned in the NIST definition, ==multi-tenancy== is a **fundamental concept in cloud computing**.

```ad-abstract
title: Definition Tenancy

==Multi-tenancy== is a model where multiple independent customers (tenants) share the same application or infrastructure, while their data and configurations remain logically isolated from one another.
```

Simply put, it means that a single set of resources serves multiple, unaffiliated tenants.
Hardware resources are shared among tenants through hardware virtualization.

```ad-example
A common example is web-server multi-tenancy, where a single server hosts multiple unrelated websites.

```

![[M38.png]]

## Measured Service
- **Service Level Agreement (SLA)**: Formal agreement (contract) between a provider and a consumer of a service, defining  
- **Service Level Indicator (SLI)**: metric that can be monitored, e.g., response time, or uptime 
- **Service Level Objective (SLO)**: a predicate over a set of SLIs condition on a measure of a specific metric (e.g., mean response time <= 1 s)  
- **penalty** and/or **compensation** in case of SLA violation

>Uptime: the most common SLI for Cloud services: https://uptime.is/

```ad-example
Example of SLA is a fixed threshold on a single SLI, 
“monthly uptime percentage for a VM is at least 99.99%” (system-level indicator) “At least 90% or requests have a response time less than 100 ms” (application-level indicator)  Not given by cloud providers 
```

## Rapid Elasticity
Elasticity is the degree to which a system can adapt to workload changes by provisioning and de-provisioning resources in an autonomic manner, such that at each point in time the available resources match the current demand as closely as possible

![[M39.png]]

### Type of Workloads
The demand of service can change in different ways.
![[M40.png]]
![[M41.png]]

### Type of Workloads: Constant
![[M42.png]]

### Type of Workloads: Periodic
![[M43.png]]

### Type of Workloads: Unpredictable
![[M44.png]]

###  Type of Workloads: Changing
![[M45.png]]

### ELASTICITY AND AUTO-SCALING

```ad-success
title: Goal
Allocate the minimum number of instances that meet the required SLA (this is called horizontal scaling)

```

But how?  Unless the traffic is regular (e.g. periodic), the main strategy is to forecast the demand of resources. Then, scaling can be done manually (not practical) or automatically. Automatic scaling aka auto-scaling can be seen as a feature of self-adaptive software systems.

![[M46.png]]

```ad-example
title: Example Scaling in AWS
![[M47.png]]

```

#### AUTOSCALING (OVER-PROVISIONING)
Although auto-scalers are indispensable parts of modern cloud deployments and determine the service quality and cost of a cloud application in dynamic workloads, effective tuning is not trivial.  The following plots report an experiment of an auto-scaler taking 30 s to scale and a new instance is lunched if the CPU load is higher than 80%, and removed if less than 25%. This result in over-provisioning because when the traffic is low again the number of replicas remains high to 5. The auto-scaler takes a new decision before the effect of the previous decision is visible (see * for details).

![[M48.png]]
#### AUTOSCALING (UNDER-PROVISIONING)
In this case the load decreases linearly, the auto-scaler initially removes too many replicas (the deploy time is 60 s) and then it adds replicas again.

![[M49.png]]

#### AUTO-SCALING CHALLENGES
- Scaling a stateful service is even more challenging. 
- In recent years, ML based auto-scaler is becoming studied 
- Reinforcement Learning seeks to identify the optimal scaling policy, e.g. it modifies the thresholds 

![[M50.png]]
![[M51.png]]

```ad-example
title: Another example in AWS
![[M52.png]]

```

## Cloud Monitoring
- **Goal:** To track the health and performance of deployed systems and services.
- **Tools:** Monitoring tools measure system-oriented metrics such as:
    - CPU utilization
    - Disk utilization and throughput (MB/s)
    - Memory usage and available memory
    - Network interface statistics
- **Providers:** Most cloud providers offer their own monitoring tools (e.g., Amazon CloudWatch), while other third-party tools are also widely used (e.g., Prometheus).
- **Challenges:**
    - It can be difficult to measure application-oriented metrics, such as response time.
    - Service Level Agreements (SLAs) are sometimes unclear; for example, "availability" is often presented as an average, which can hide short but impactful outages over a long period.
    - Detecting SLA violations is not always straightforward.
    - Data durability is never guaranteed to be 100%, and ensuring data backup and integrity is ultimately the user's responsibility.

## Broadband Access
Cloud resources accessed over Internet using standard access mechanisms that provide platform- independent access, e.g. published service interface/APIc.

## Main Cloud Providers
![[M53.png]]

----
----
----

# Behind IAAS
IaaS are evolution of classic Data Center (DC). A DC is a controlled, secure environment ensuring continuous and reliable digital services. It includes:
- **Cooling Systems**: air conditioning and centralized cooling to maintain optimal temperature.
- **Power supply**: stable electrical power with backup systems.
- **Fire Protection**: sprinklers or gas-based systems to prevent equipment damage
- **Security**: personnel, access control, surveillance, and other protective measures.

## Data Center Technology
A DC transform energy into computation
![[M54.png]]

## Computing Units
The hardware building blocks of a DC are low-end servers, with rack enclosure (rack-mounted) or a blade enclosure. 

**Rack-mounted servers**
Sono server **“autonomi”**, cioè ognuno ha **tutti i componenti necessari per funzionare da solo**. Vengono montati nei rack, cioè armadi metallici verticali che contengono più server uno sopra l'altro. Ogni rack ha spazi standardizzati detti Racks Units (U o RU)
- 1U = 44,45mm altezza
- 2U = 88,9mm altezza

**Blade Servers**
I blade sono server sottili (come schede) che non possono funzionare da soli. Si inseriscono in un blade enclosure, cioè un contenitore che fornisce:
- alimentazione elettrica comune
- raffreddamento
- connessioni di rete
Dato che non hanno alimentatore e ventole, occupano meno spazio e sono più densi

```ad-example
- Serve grade hardware (designed for 24/7 operation)
- Mainboards usually contain > 2 CPUs per board and have large caches
-  RAM sizes are usually very large in site (> 1TB)
  NIC are usually equiped with multiple ports, different port specifications and have high bandwidhts
-  Storage capabilities are usually designed for fault tolerance and performance 
![[Pasted image 20251006115017.png]]

```

### Rack of Servers
A standard rack consists of a payload bay (vano) to usually host 42 units (server, storage) and networking devices (switches, routers) known as ToR (Top o Rack) switch. Communication occurs among servers inside the same rack, or with external endpoints.

![[M56.png]]

### Networking
The traffic is not confined within servers of the same rack; rather, it can be directed to other racks (east–west traffic) or outside the DC (north–south traffic).

To avoid communication bottleneck, the commutation topology is hierarchical (fat-tree of leaf-span). In addition, new communication protocols that allow parallel multi-path communications can be used instead of single path, TCP

![[M57.png]]

An **_Availability Zone (AZ)_** is a name used to denote single physical data center DC, or more often, a group of physically separate data centers located close to each other, sharing network infrastructure and low-latency connectivity.
-  AZ further aggregated in regions (a region usually has 2–6 Azs)
- Latency is lower for users of that region
- To increase availability, user traffic can be distributed among different AZ of a region using an Application (level) Load Balancer (ALB)

#### Lead-Spine Topology
![[M58.png]]

### Virtual Private Cloud
A Virtual Private Cloud (VPC) is a set of subnets in different DCs
![[M59.png]]

```ad-example
Google Cloud’s infrastructure follows a similar philosophy:
- The infrastructure is based in five major geographic locations: North America, South America, Europe, Asia, and Australia, connected via high-speed networks and subsea cables
- Locations are currently divided into 40 regions and regions into 121 zones
  
  ![[M60.png]]

```

## Type of Servers
- **_Web Server_**: Designed for the hosting of websites, support web standards and frameworks
- **_Database Server_**: Specialized for data storage and retrieval (Relational/NoSQL). Concurrent access of data by users.
- **_File Server_**: Serves files or file systems to clients. Supports standard protocols (FTP/S)
- **DNS Server**: Specialized for the name resolution in computer networks. Functionality by DNS-Software.

### Server Virtualization
```ad-abstract
title: Definition
La **server virtualization** consiste nel suddividere un **server fisico** (bare metal) in più **server virtuali** (VM), ognuno dei quali funziona come se fosse una macchina fisica indipendente.  
In questo modo, più sistemi operativi e applicazioni possono essere eseguiti contemporaneamente sullo stesso hardware, migliorando l’efficienza e riducendo i costi.

```

**Bare metal sever**
- One standalone physical server with one dedicated OS installed on the server
- Exclusive access to all hardware resources (CPU, RAM, storage, networks)
- Suitable for high performance, because of direct access to hardware capabilities
- Drawbacks
	- Management and maintenance is complex
	- Management and maintenance is very expensive
	- High cost for operation of servers
	- Dedicated usage of server leads to many idle times

**VM Server**
- Virtual server, which a ‘slice’ of the bare metal server
- It acts like a hw server, i.e. allows to run applications that usually require a dedicated server

**HW VIRTUALIZATION**
L’hardware virtualization consiste nel virtualizzare le risorse fisiche di un server (**host**) per creare una o più **macchine virtuali (VM)**, che si comportano come macchine fisiche indipendenti (**guest**). Questo è reso possibile da un software chiamato **Virtual Machine Manager (VMM)** o **Hypervisor**.

Ogni VM dispone di una **CPU virtuale (vCPU)**, **memoria**, **dispositivi di I/O** e **interfacce di rete** virtuali, replicando in tutto e per tutto l’ambiente di un computer reale.

A differenza dei sistemi multiutente, dove più utenti condividono lo stesso sistema operativo e possono potenzialmente interagire tra loro (vedendo processi o risorse comuni), le VM garantiscono **un isolamento molto più elevato**: ogni macchina virtuale è completamente separata dalle altre e dal sistema host, riducendo il rischio che un attacco a un utente comprometta l’intero sistema.

### Machine Reference Model
![[M61.png]]

### Virtual Machine Manager
![[M62.png]]

### VMM and Privileged Instructions
**Istruzioni privilegiate** sono quelle che possono modificare lo stato della CPU fisica (pCPU).
Se un guest (VM) eseguisse direttamente queste istruzioni, cambierebbe lo stato della **pCPU** e quindi influenzerebbe tutti gli altri guest e l’host.
Perciò il comportamento desiderato è che quelle istruzioni **modifichino solo lo stato della vCPU** (la CPU virtuale visibile al guest), **non** lo stato reale (pCPU).

#### NOISY NEIGHBOURS
- Depending on the load on the other VMs, cache miss rate may for example increase, network bandwidth decrease, etc, (‘noisy neighbours’)
- In general, when the number of VMs increases behind the real pCPU capabilities, e.g. due to VM overcommitment, the vCPU clock runs at lower rate
- Wall clock correction

![[M63.png]]

#### BENEFIT OF VM
-  High isolation among tenants
- Server consolidation
- VM management

- Templating – create an OS + application VM, provide it to customers, use it to create multiple instances of that combination
- Live migration – move a running VM from one host to another
	- No interruption of user access

![[M64.png]]

### Implementation Options
Diversi modi in cui può essere realizzata la virtualizzazione  (**diverse architetture o tecnologie** che permettono di eseguire più sistemi operativi o applicazioni su un’unica macchina fisica.)

**_Type 0 hypervisors_** are hardware-based solutions that create virtual machines through physical hardware partitioning. They do not manage virtual machines or support features like migration; instead, they simply divide and allocate hardware resources to different operating systems. Examples include IBM LPARs and Oracle LDOMs, which are typically used on mainframes or high-end servers.

**_Type 1 hypervisors_** - are software systems similar to operating systems, designed specifically for virtualization. They run directly on the hardware and manage virtual machines efficiently. Examples include VMware ESX, Citrix XenServer, and the AWS Nitro Hypervisor, which also uses custom hardware components.

**_Type 1 hypervisors_** – includes general-purpose operating systems that integrate virtualization functions within the kernel. These systems work as both a standard OS and a virtual machine manager. Examples are Microsoft Windows Server with Hyper-V and Red Hat Linux with KVM.

**_Type 2 hypervisors_** - are applications installed on top of a standard operating system. They allow users to run guest operating systems inside virtual machines while relying on the host OS for hardware access. Common examples include VMware Workstation, VMware Fusion, Parallels Desktop, and Oracle VirtualBox.

Other variations include:
- Paravirtualization - Technique in which the guest operating system is modified to work in cooperation with the VMM to optimize performance
- Emulators – Allow applications written for one hardware environment to run on a very different hardware environment, such as a different type of CPU

**_Application containment_** - provides virtualization-like features by segregating applications from the operating system, making them more secure, manageable
- Including Oracle Solaris Zones, BSD Jails, and IBM AIX WPARs
- Linux Containers (LXC)
- Docker containers


```ad-example
title: Live migration of VM
![[M65.png]]

```

```ad-example
title: Example EC2
![[M66.png]]

```

### Building blocks of a VMM
Most VMMs implement a virtual CPU (vCPU) to represent state of CPU per guest as guest believes it to be:
- When guest context switched onto CPU by VMM, information from vCPU loaded and stored (much like processes in a OS, vCPU like PCB Process Control Block )
- Most of the binary instructions are performed without any change by the physical CPU (pCPU)
Several techniques

## BASICS OF THE X86 ARCHITECTURE
In the x86 architecture, CPUs use a system of four privilege levels, called _rings_, which are tracked by a register known as the **Current Privilege Level (CPL)**. The CPL defines the current operating mode of the processor.

When the CPU operates in **ring 0**, also called **kernel mode**, it has full access to all hardware resources and can execute any machine instruction. The operating system kernel runs in this mode so it can manage hardware directly.

In contrast, **ring 3**, or **user mode**, has restricted privileges. Applications running in user mode cannot perform sensitive operations, such as directly accessing hardware or modifying system settings.

Modern operating systems typically use only **ring 0** for the kernel and **ring 3** for user applications, while rings 1 and 2 remain unused. When a user-mode program needs to perform a privileged action, it requests the kernel’s help through a **system call**. This triggers an exception that switches the CPU from ring 3 to ring 0, allowing the kernel to safely execute the requested operation before returning control to the user process.

![[M67.png]]
## BUILDING BLOCK – TRAP AND EMULATE
A virtual machine (VM) requires two operational modes, similar to a physical CPU: **virtual user mode** and **virtual kernel mode**. In the **trap-and-emulate** approach, the guest operating system runs in real user mode, and any action that would normally switch the OS into kernel mode instead triggers a switch to the virtual kernel mode.

This switch occurs when the guest attempts to execute a **privileged instruction** in user mode. The CPU generates an error, or **trap**, which transfers control to the Virtual Machine Monitor (VMM). The VMM then analyzes the instruction, performs the operation on behalf of the guest, and returns control to the guest in user mode.

Code running in guest user mode executes at nearly the same speed as on a physical machine, but **kernel-mode operations run slower** because each privileged instruction must be trapped and emulated by the VMM. This slowdown becomes more significant when multiple guest VMs are running simultaneously, each requiring frequent trap-and-emulate operations. To address this, modern CPUs provide **hardware support for virtualization**, adding modes and features that reduce the overhead and improve the performance of kernel-mode operations in VMs.

### Virtualization Implementation
![[M68.png]]


```ad-example
![[M69.png]]

```

## POPEK AND GOLDBERG VIRTUALIZATION REQUIREMENTS
In 1974, Popek and Goldberg defined conditions that a computer architecture must meet to support **efficient system virtualization**. They classified machine instructions into three types. **Privileged instructions** execute normally in supervisor (kernel) mode but cause a trap if executed in user mode. **Sensitive instructions** either modify critical system resources, such as performing I/O or changing page tables, or reveal information about the current privilege level, which could indicate that a guest OS is not running directly on physical hardware. **Innocuous instructions** are neither sensitive nor privileged and have no impact on virtualization.

According to Popek and Goldberg, a necessary condition for virtualization is that the set of sensitive instructions must be a **subset of the privileged instructions**. In other words, every instruction that could affect system resources or reveal the virtualization layer must trap when executed outside kernel mode so that the Virtual Machine Monitor (VMM) can safely handle it.