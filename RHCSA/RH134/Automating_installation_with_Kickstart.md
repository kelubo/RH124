# Chapter 1 Automating Installation with Kickstart
<table border="0">
<tr>
  <th align="left" colspan="3">概述</th>
</tr>
<tr>
  <td>Goal</td>
  <td>To automate the installation of Red Hat Enterprise Linux System with Kickstart</td>
</tr>
<tr>
  <td>Objectives</td>
  <td>Explain Kickstart concepts and architecture.Create a Kickstart configuration file.</td>
</tr>
<tr>
  <td>Sections</td>
  <td>Defining the Anaconda Kickstart System(and Practice).Deploying a New Virtual System with Kickstart(and Practice)</td>
</tr>
<tr>
  <td>Chapter Test</td>
  <td>Automating installation with Kickstart</td>
</tr>
</table>
## Defining the Anaconda Kickstart System
### Objectives
After completing this section,students should be able to identify key configuration elements found inside a Kickstart configuration file.
### Introduction to Kickstart installations
A system administrator can automate the installation of Red Hat Enterprise Linux using a feature called Kickstart.Anaconda,the Red Hat installer,needs to be told how to install a system:partition disks,configure network interfaces,select which packages to install ,etc.This is an interactive process by default.A Kickstart installation uses a text file to provide all of the answers to these questions,so no interaction is required.
>Comparison  
>Kickstart in Red Hat Enterprise Linux is similar to Jumpstart for Oracle Solaris,or to an unattended installation for Microsoft Windows.  

Kickstart configuration files begin with a list of commands that define how the target machine is to be installed.Lines that start with # characters are comments that are ignored by the installer.Additional sections begin with a line that starts with a % character and end with a line with the %end directive.

The %packages section specifies the software to be installed on the target system.Individual packages are specified by name (without versions).Package groups can be specified by name or ID,and start with an @ character.Environment groups (groups of package groups) can be specified with the @^ followed immediately by the name or ID of the environment group.Groups have mandatory,default,and optional components.Normally,mandatory and default components will be installed by Kickstart.Package or group names that are preceded with a - character are excluded from installation unless they are mandatory or installed due to RPM dependencies form other packages.

Two additional sections are the %pre and %post scripts.%post scripts are more common.They configure the system after all of the software has been installed.The %pre script is executed before any disk partitioning is done.  
The configuration commands must be specified first.The %pre,%post,and %packages can occur in any order after the configuration commands.
### Kickstart configuration file commands
Installation commands  

* url:Specifies the location for the installation media.  
Example:  
`url --url="ftp://installserver.example.com/pub/RHEL7/dvd"`
* repo:This iption tells Anaconda where to find the packages for installation.This option must point to a valid yum repository.  
Example:  
`repo`
* 