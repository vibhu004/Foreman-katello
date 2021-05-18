# Content Management Guide

### 1. Introduction
In the context of Foreman, content is defined as the software installed on systems. 

Foreman manages the following content:

* Subscription management
This provides organizations with a method to manage their subscription information.

* Content management
This provides organizations with a method to store content and organize it in various ways.

### 2. Types of Content
* RPM  Packages
* Deb Packages
* Conatiner image
* Files

### 3. Basic content management workflow
This is a quick overview of the tasks involved in the basic content management workflow in Foreman. If you have installed Foreman with Katello and want to synchronize and manage Enterprise Linux content on your hosts, follow the steps in this chapter.
Create repository to mirror content from CentOS Stream.

<ol type=A>
<li>Synchronize the Content.</li>
<li>Create Activation Keys.</li>
<li>Register Hosts to consume this content.</li>
<li>Manage RPMs on hosts using the katello-agent.</li>
</ol>

### A. Creating repositories to synchronize
Use this procedure to discover available repositories in the CentOS Stream, then select the repositories to mirror into a product.

Procedure

1.  In the Foreman web UI, navigate to Content > Products.
2.  Click Repo Discovery.
3. In the Repository Type field, select Yum Repositories.
4. In the URL to Discover field, enter the CentOS Stream URL http://mirror.centos.org/centos/8-stream.
5. Click Discover.
6. Select /AppStream/x86_64/os/ and /BaseOS/x86_64/os/ repositories.
7. Click Create Selected.
8. In the Product field select New Product.
9. In the Name field enter CentOS Stream or desired product name.
10. Click Run Repository Creation.

To view your newly created product, navigate to Content > Products, and select the name of the new product.

### B. Synchronizing content from an upstream repository
Use the following procedure to mirror the contents of the upstream Centos repositories.

Procedure

1. In the Foreman web UI, navigate to Content > Products
2. Select your new CentOS Stream product from the previous procedure.
3. Locate the AppStream x86_64 os and BaseOS x86_64 os repositories.
4. Select both repositories
5. Click Sync Now

###C. Creating an Activation Key
Use the following procedure to create an activation key that you can use to subscribe your hosts to content managed by Foreman.

1. In the Foreman web UI, navigate to Content > Activation keys and click Create Activation Key.
1. In the Name field, enter the name of the activation key.
1. In the Description field, enter a description for the activation key.
1. From the Environment list, select the Library.
1. From the Content View list, select Default Organization View.
1. Click Save.
1. Click on the Subscriptions tab on the Activation Key’s details page.
1. Click on the Add tab.
1. Select all the product subscriptions in the table.
1. Click Add Selected to save.

<! -- 
### D. Registering a CentOS Stream host to Foreman
Use the following procedure to register an existing CentOS Stream host to Foreman

1. Log on to the Centos 8 host you want register.
2. Download the consumer RPM for your Foreman server.
3. This is located in the pub directory on Foreman server’s web server. For example, for a Foreman server with the host name foreman.example.com, enter the following command on the host to register:

```bash
# rpm -Uvh http://foreman.example.com/pub/katello-ca-consumer-latest.noarch.rpm
```

This RPM installs the necessary certificates for accessing repositories on Foreman server and configures Red Hat Subscription Manager to use the server’s URL.

4. On the host, enter the following command to register the host to Foreman using the activation key:

```bash
# subscription-manager register --activationkey="My_Activation_Key"  --org="My_Organization"
```

5. After registration, enter the yum repolist command to update /etc/yum.repos.d/redhat.repo and enable content from Foreman server.

```bash
# yum repolist

repo id                                                           												repo name
Default_Organization_Centos_Stream_AppStream_x86_64_os            AppStream x86_64 os
Default_Organization_Centos_Stream_BaseOS_x86_64_os               BaseOS x86_64
Uploading Enabled Repositories Report
```

6. Check the /etc/yum.repos.d/redhat.conf and ensure that the appropriate repositories have been enabled.
--> 
