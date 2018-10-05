## UNDERSTANDING PAM FOR LINUX

1. Most of this file is not my original work and is created by copying important stuff from the official documentation of `pam-1.1.1` installed by default with the last RHEL 6.10 release.

- As this release of RHEL is the last minor release of RHEL 6 major release candidate, I updated the whole  RHEL 6.10 system and then extracted the contents so I beleive that this file will remain current for systems based on RHEL 6.


- Linux-PAM (**Pluggable Authentication Modules for Linux**) is a suite of shared libraries that enable the local system administrator to choose how applications authenticate users.

- In other words, without rewriting and recompiling a PAM aware application, it is possible to switch between the authentication mechanisms it uses.

- It is the purpose of the Linux-PAM project to separate the development of privilege granting software from the development of secure and appropriate authentication schemes.

- This is accomplished by providing a library of
functions that an application may use to request that a user be authenticated.

- This PAM library is configured locally with a system file, `/etc/pam.conf` or a series of configuration files located in `/etc/pam.d/` to authenticate a user
request via the locally available authentication modules. 
    
    The modules themselves will usually be located in the directory `/lib/security` or `/lib64/security` and take the form of dynamically loadable object files.

- The flexibility of Linux-PAM is that you have the freedom to stipulate which authentication scheme is to be used. You have the freedom to set the scheme for any/all PAM aware applications on your Linux system.


- Linux-PAM deals with four separate types of management  tasks, these are:

    1. Authentication management.
    - Account management.
    - Session management.
    - Password management.


- Here is a figure that describes the overall organization of Linux-PAM: 
    ![alt text](https://github.com/divyanshtiwarijpr/docs-linux-rhel/blob/master/rhel-6-pam/organization.PNG)
