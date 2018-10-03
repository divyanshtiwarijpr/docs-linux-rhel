## *RPM* PACKAGE MANAGER

<br>

1. **RPM** which stands for **R**PM **P**ackage **M**annager is a package management system which can be used to build, install, verify, update and erase **individual software packages**.

- A **package** is an **archive of files** required for any software to run and **metadata about the package file itself**. Generally `.rpm` packages are `gzip` compressed `cpio` acrhives.

    The **metadata** includes descriptive information about the package such as package name, package version, summary about the package, helper scripts, file attributes etc.

    There are **two types of packages**:

    1. **Binary** packages: These type of packages contain the pre compiled software to be installed as is in binary form along with the configuration files. These are distributed as `.rpm` files.
    
    - **Source** packages: These type of packages contain the source code necessary to produce binary packages. These allow the user to manually compile, review and modify the source code These are generally distrubuted as `.srpm` files.

- The `rpm` command with the general and action specific options is used to manipulate the individual software packages. This command requires root privileges to run and thus user must be cautious when using this command. Using this command in a careless manner can make a system unstable and even unable to boot.

- To view a short usage summary type `rpm` without any options   

- **Global Options**

    These options are also known as general option and are applicable to all the `rpm` commands including all action specific commands.

    `--help` <br> Display a short help messhage.

    `--version` <br> Print the version number of `rpm` itself. 

    `--quiet` <br> Print as little as possible.

    `-v` <br> Print verbose information.

    `-vv` <br> Print debugging information.

    `--pipe COMMAND`<br> Pipes the output of rpm to the command COMMAND.

  
- **Install, Upgrade and Freshen Options**

    `rpm {-i|--install} [install-options] PACKAGE_FILE/FILES` <br>
    This installs a new package and different versions of the package can be installed

    `rpm {-U|--upgrade} [install-options] PACKAGE_FILE/FILES`

    `rpm {-F|--freshen} [install-options] PACKAGE_FILE/FILES`





   