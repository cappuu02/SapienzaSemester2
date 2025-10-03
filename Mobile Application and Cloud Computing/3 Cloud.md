
```ad-abstract
title: Cloud
The name “**_Cloud Computing_**” evokes the cloud as an iconic representation of the Internet (a cloud is often used to represent a network), and computing to indicate the resources required to perform computation, such as storage, CPUs, and memory. 

In simple terms, cloud computing refers to the shift of computing from a single server or data center to an equivalent service accessed via the Internet.

```

# NIST Definition of cloud computing
![[Pasted image 20251003123613.png]]

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

![[Pasted image 20251003124107.png]]
# THE INITIAL COMPUTING SERVICE FROM AWS
Cloud computing age started in 2006 with Amazon Web Services (AWS)’s Elastic Cloud Computing (EC2) and Simple Storage Systems (S3), plus a Simple Queue Service (SQS)
- `EC2` service allows to use provision size variable VMs
- `S3` is an object storage service (data are stored as objects into beckets), e.g. images, or web site Ensure scalability, data availability, security
- `SQS`, messaging system used to connect other components

![[Pasted image 20251003124206.png]]

# SERVICE FEATURES
![[Pasted image 20251003124226.png]]

## On-Demand Self-Service
The on-demand service feature refers to the ability to consume the computing facility as much as needed at any moment, i.e., through a user-friendly UI or programmatically, e.g. python script, or Infrastructure as Code (IaC) .

The requested cloud services is provisioned in a short period of time and without any need of human intervention at vendor’s end. 

```ad-example
title: Example from AWS
1. Sign in to the management console (aws) 
2. Open EC2 console choosing EC2 under compute 
   ![[Pasted image 20251003132755.png]]
3. Select a AWS Region
   ![[Pasted image 20251003132819.png]]
4. Lunch the instance 
   
![[Pasted image 20251003132853.png]]

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

![[Pasted image 20251003133252.png]]

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

![[Pasted image 20251003133528.png]]

### Type of Workloads
The demand of service can change in different ways.
![[Pasted image 20251003133627.png]]
![[Pasted image 20251003133656.png]]

### Type of Workloads: Constant
![[Pasted image 20251003133815.png]]

### Type of Workloads: Periodic
![[Pasted image 20251003133834.png]]

### Type of Workloads: Unpredictable
![[Pasted image 20251003133859.png]]

###  Type of Workloads: Changing
![[Pasted image 20251003133930.png]]

### ELASTICITY AND AUTO-SCALING

```ad-success
title: Goal
Allocate the minimum number of instances that meet the required SLA (this is called horizontal scaling)

```

But how?  Unless the traffic is regular (e.g. periodic), the main strategy is to forecast the demand of resources. Then, scaling can be done manually (not practical) or automatically. Automatic scaling aka auto-scaling can be seen as a feature of self-adaptive software systems.

![[Pasted image 20251003134210.png]]

```ad-example
title: Example Scaling in AWS
![[Pasted image 20251003134247.png]]

```

#### AUTOSCALING (OVER-PROVISIONING)
Although auto-scalers are indispensable parts of modern cloud deployments and determine the service quality and cost of a cloud application in dynamic workloads, effective tuning is not trivial.  The following plots report an experiment of an auto-scaler taking 30 s to scale and a new instance is lunched if the CPU load is higher than 80%, and removed if less than 25%. This result in over-provisioning because when the traffic is low again the number of replicas remains high to 5. The auto-scaler takes a new decision before the effect of the previous decision is visible (see * for details).

![[Pasted image 20251003134342.png]]
#### AUTOSCALING (UNDER-PROVISIONING)
In this case the load decreases linearly, the auto-scaler initially removes too many replicas (the deploy time is 60 s) and then it adds replicas again.

![[Pasted image 20251003134409.png]]

#### AUTO-SCALING CHALLENGES
- Scaling a stateful service is even more challenging. 
- In recent years, ML based auto-scaler is becoming studied 
- Reinforcement Learning seeks to identify the optimal scaling policy, e.g. it modifies the thresholds 

![[Pasted image 20251003134501.png]]
![[Pasted image 20251003134514.png]]

```ad-example
title: Another example in AWS
![[Pasted image 20251003134556.png]]

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
![[Pasted image 20251003134737.png]]