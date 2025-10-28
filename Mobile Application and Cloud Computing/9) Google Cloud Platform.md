# GCP Introduction

 Google Cloud Platform is based on a set of distributed and interconnected Data Centers. 
 The DC are divided in **_five major geographic locations_**: 
 - North America, 
 - South America, 
 - Europe, 
 - Asia, 
 - Australia
 These Data Centers are connected via high-speed networks and subsea cables. Locations are currently divided into $40$ regions and regions into $121$ zones.

```ad-note
title: Region
A geographical region within the world (typically a city) in which at least 3 physical or logical data centers located in different zone. An example of a region is europe-west2, which is located in London, or europe-west8 in Milan.

```

```ad-note
title: Zone
A logical or physical data center (a building with computers in it) in which cloud resources physically reside. An example of a zone is europe-west2-c.

```

![[M129.png]]

# Resources
```ad-note
title: Definition
A resource is any component or object that can be managed, configured, or used within the GCP, such as computers and hard disk drives, and virtual resources, such as virtual machines (VMs)

```

![[M130.png]]

# Global, Regional and Zonal Resources
==Zonal resources== can be accessed only by resources that are in the same zone. (VM instances can mount disks in the same zone.)

==Regional resources== can be accessed only by resources that are located in the same region. (Private subnet network, Artifact Registry) 

==Global resources== can be accessed by any other resource, across regions and zones. (External static IP address, firewall rules, load balancer...)


# Projects
Any Google Cloud resources must belong to a project. Each Google Cloud project has the following:
- ==Project name==:  human readable name.
- ==Project ID==: alpha-numeric string identifier for the project (can be changed).
- ==Project number==: a long number that also identifies the project but is rarely used (it is an internal identifier). provided automatically. 

![[M131.png]]

![[M132.png]]

# Identity and Access Management
==IAM (Identity and Access Management)== is Google Cloud’s system to control who can do what on cloud resources.
1. **_Resource_**: project, bucket, VM, repository, etc. 
2. **_Member_**: user, group, service account, domain 
3. **_Permission_**: defines what actions can be performed on a resource 
4. **_Role_**: collection of permissions 
5. **_Policy_**: association of member + role + resource 

## Members
- **_Individual users_**: `user:alice@company.com `
- **_Groups_**: `group:dev-team@company.com `
- **_Service accounts_**: `serviceAccount:my-service-account@project.iam.gserviceaccount.com `
- **_Domains_**: `domain:company.com `
- **_Public_**: allUsers, allAuthenticatedUsers (use with caution) 

## Type of roles
- **_Basic roles_**: Owner, Editor,Viewer
- **_Predefined roles_**: service-specific (Cloud Run Admin, Storage Object Viewer, Artifact Registry Reader)
- **_Custom roles_**: user-defined roles with specific permissions 

![[M133.png]]

## Permissions
```ad-seealso
title: Definition
Permission defines what actions a member can perform on a resource.

```

```ad-example
compute.instances.get → read VM information 
storage.objects.create → upload objects to a bucket 
artifactregistry.repositories.downloadArtifacts → pull Docker images 

```

## Policy
```ad-seealso
title: Definition
Policy is a set of rules (bindings) rule stating which members have which roles on which resources.

```

```ad-example
![[Pasted image 20251027124121.png]]

```

# GCP Access
Google cloud Platform access work like this:
![[M135.png]]

- ==Google cloud console==: It's a web-based graphical interface that allows you to intuitively manage Google Cloud projects and resources. All operations can be performed through a point-and-click interface.
- ==Cloud Shell==: It offers a preconfigured terminal environment accessible directly from your browser. It already includes the tools needed to interact with GCP, such as the gcloud CLI.
- ==gcloud CLI:== È l’interfaccia a riga di comando che permette di gestire e automatizzare risorse e flussi di lavoro su Google Cloud. Può essere utilizzata in due modalità:
	- **Dal browser**, tramite Cloud Shell.
	- **In locale**, installando il **Google Cloud SDK** sulla propria macchina (autenticazione richiesta).
	I comandi della CLI possono essere facilmente integrati in **script** per automatizzare attività ripetitive e semplificare la gestione dei progetti.