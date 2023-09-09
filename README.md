

Red Hat Enterprise Linux 8 content is distributed through the two main repositories: BaseOS and AppStream.

The BaseOS repository contains the core set of the underlying operating system functionality that provides the foundation for all installations. 

The AppStream repository contains additional user-space applications.

Components made available as Application Streams can be packaged as modules or RPM packages, and are delivered through the AppStream repository in Red Hat Enterprise Linux 8.

Content in the AppStream repository is packaged in two ways :

1. Individual RPM packages

2. Traditional RPM packages available for immediate installation.
   

Modules :

Modules are collections of packages representing a logical unit: an application, a language stack, a database, or a set of tools. 

#### To list module streams available to your system, use:

```
[root@ip-172-31-32-210 ~]# yum module list
Updating Subscription Management repositories.
Unable to read consumer identity

This system is not registered with an entitlement server. You can use subscription-manager to register.

Red Hat Enterprise Linux 9 for x86_64 - AppStream from RHUI (RP  26 MB/s |  24 MB     00:00    
Red Hat Enterprise Linux 9 for x86_64 - BaseOS from RHUI (RPMs)  22 MB/s |  13 MB     00:00    
Red Hat Enterprise Linux 9 Client Configuration                  29 kB/s | 3.4 kB     00:00    
	Red Hat Enterprise Linux 9 for x86_64 - AppStream from RHUI (RPMs)
Name       Stream Profiles                       Summary                                        
maven      3.8    common [d]                     Java project management and project comprehensi
                                                 on tool                                        
nginx      1.22   common [d]                     nginx webserver                                
nodejs     18     common [d], development, minim Javascript runtime                             
                  al, s2i                                                                       
php        8.1    common [d], devel, minimal     PHP scripting language                         
postgresql 15     client, server                 PostgreSQL server and client module            
ruby       3.1    common [d]                     An interpreter of object-oriented scripting lan
                                                 guage                                          

Hint: [d]efault, [e]nabled, [x]disabled, [i]nstalled

```

#### To display details about a module, including a description, a list of all profiles, and a list of all provided packages, use:

```
[root@ip-172-31-32-210 ~]# yum module info postgresql
Updating Subscription Management repositories.
Unable to read consumer identity

This system is not registered with an entitlement server. You can use subscription-manager to register.

Last metadata expiration check: 0:00:28 ago on Sat 09 Sep 2023 03:43:06 AM UTC.
Name             : postgresql
Stream           : 15
Version          : 9020020230213093256
Context          : rhel9
Architecture     : x86_64
Profiles         : client, server
Default profiles : 
Repo             : rhel-9-appstream-rhui-rpms
Summary          : PostgreSQL server and client module
Description      : PostgreSQL is an advanced Object-Relational database management system (DBMS). The postgresql-server package contains the programs needed to create and run a PostgreSQL server, which will in turn allow you to create and maintain PostgreSQL databases. The base postgresql package contains the client programs that you'll need to access a PostgreSQL DBMS server.
Requires         : platform:[el9]
Artifacts        : pg_repack-0:1.4.8-1.module+el9.2.0+17405+aeb9ec60.src
                 : pg_repack-0:1.4.8-1.module+el9.2.0+17405+aeb9ec60.x86_64
                 : pg_repack-debuginfo-0:1.4.8-1.module+el9.2.0+17405+aeb9ec60.x86_64
                 : pg_repack-debugsource-0:1.4.8-1.module+el9.2.0+17405+aeb9ec60.x86_64
                 : pgaudit-0:1.7.0-1.module+el9.2.0+17405+aeb9ec60.src
                 : pgaudit-0:1.7.0-1.module+el9.2.0+17405+aeb9ec60.x86_64
                 : pgaudit-debuginfo-0:1.7.0-1.module+el9.2.0+17405+aeb9ec60.x86_64
                 : pgaudit-debugsource-0:1.7.0-1.module+el9.2.0+17405+aeb9ec60.x86_64
                 : postgres-decoderbufs-0:1.9.7-1.Final.module+el9.2.0+17405+aeb9ec60.src
                 : postgres-decoderbufs-0:1.9.7-1.Final.module+el9.2.0+17405+aeb9ec60.x86_64
                 : postgres-decoderbufs-debuginfo-0:1.9.7-1.Final.module+el9.2.0+17405+aeb9ec60.
```


#### Enabling Modules :

```

[root@ip-172-31-32-210 ~]# yum module enable postgresql
Updating Subscription Management repositories.
Unable to read consumer identity

This system is not registered with an entitlement server. You can use subscription-manager to register.

Last metadata expiration check: 0:09:22 ago on Sat 09 Sep 2023 03:43:06 AM UTC.
Dependencies resolved.
================================================================================================
 Package               Architecture         Version                 Repository             Size
================================================================================================
Enabling module streams:
 postgresql                                 15                                                 

Transaction Summary
================================================================================================

Is this ok [y/N]: y
Complete!
[root@ip-172-31-32-210 ~]# yum module list
Updating Subscription Management repositories.
Unable to read consumer identity

This system is not registered with an entitlement server. You can use subscription-manager to register.

Last metadata expiration check: 0:09:34 ago on Sat 09 Sep 2023 03:43:06 AM UTC.
Red Hat Enterprise Linux 9 for x86_64 - AppStream from RHUI (RPMs)
Name       Stream Profiles                       Summary                                        
maven      3.8    common [d]                     Java project management and project comprehensi
                                                 on tool                                        
nginx      1.22   common [d]                     nginx webserver                                
nodejs     18     common [d], development, minim Javascript runtime                             
                  al, s2i                                                                       
php        8.1    common [d], devel, minimal     PHP scripting language                         
postgresql 15 [e] client, server                 PostgreSQL server and client module            
ruby       3.1    common [d]                     An interpreter of object-oriented scripting lan
                                                 guage                                          

Hint: [d]efault, [e]nabled, [x]disabled, [i]nstalled

```

```

[root@ip-172-31-32-210 ~]# yum module list  --enabled
Updating Subscription Management repositories.
Unable to read consumer identity

This system is not registered with an entitlement server. You can use subscription-manager to register.

Last metadata expiration check: 0:09:41 ago on Sat 09 Sep 2023 03:43:06 AM UTC.
Red Hat Enterprise Linux 9 for x86_64 - AppStream from RHUI (RPMs)
Name              Stream        Profiles              Summary                                   
postgresql        15 [e]        client, server        PostgreSQL server and client module       

Hint: [d]efault, [e]nabled, [x]disabled, [i]nstalled
```

#### Disabling modules

```
[root@ip-172-31-32-210 ~]# yum module disable postgresql
Updating Subscription Management repositories.
Unable to read consumer identity

This system is not registered with an entitlement server. You can use subscription-manager to register.

Last metadata expiration check: 0:12:18 ago on Sat 09 Sep 2023 03:43:06 AM UTC.
Dependencies resolved.
================================================================================================
 Package               Architecture         Version                 Repository             Size
================================================================================================
Disabling modules:
 postgresql                                                                                    

Transaction Summary
================================================================================================

Is this ok [y/N]: y
Complete!
[root@ip-172-31-32-210 ~]# yum module list  --enabled
Updating Subscription Management repositories.
Unable to read consumer identity

This system is not registered with an entitlement server. You can use subscription-manager to register.

Last metadata expiration check: 0:12:31 ago on Sat 09 Sep 2023 03:43:06 AM UTC.
```
