
## Creating a Vagrant Virtual Development Environment for xTuple Dashboards ##

[Vagrant](http://docs.vagrantup.com/v2/why-vagrant/index.html) is open-source software used to create lightweight
and portable virtual development environments. Vagrant works like a "wrapper" for VirtualBox that can create,
configure, and destroy virtual machines with the use of its own terminal commands. Vagrant facilitates the setup
of environments without any direct interaction with VirtualBox and allows developers to use preferred editors
and browsers in their native operating system.

Note: This document is for setting up a virtual environment on a Unix host.

###  Install Vagrant ###

- Download and install [VirtualBox 4.3.8](https://www.virtualbox.org/wiki/Download_Old_Builds_4_3)
  - Do not open VirtualBox or create a virtual machine. This will be handled by Vagrant.
- Download and install [Vagrant 1.5.0](http://www.vagrantup.com/downloads.html)
  - Package managers like apt-get and gem install will install an older version of Vagrant so it is required to use the download page.

[Fork](http://github.com/lynnaloo/xtuple-dashboard/fork) this repository on Github.

Clone this fork of the `xtuple-dashboard` respository to a directory on your host machine:

    host $ git clone https://github.com/<your-github-username-here>/xtuple-dashboard.git
    host $ cd xtuple-dashboard

### Setup Vagrant ###

- In the `Vagrantfile`, ensure that the `sourceDir` variable to matches the location of the cloned xTuple source code: `sourceDir = "../../dev"`
  - This path should be relative to the location of the Vagrantfile

### Install VirtualBox Guest Additions Plugin

    host $ vagrant plugin install vagrant-vbguest

### Connect to the Virtual Machine ###

Start the virtual machine:

    host $ vagrant up

Connect to the virtual machine via ssh:

    host $ vagrant ssh

Bundle the Ruby gems:

    vagrant $ cd xtuple-dashboard
    vagrant $ bundle install

Setup environment variables:

* Make a copy of the `.env.sample` file named `.env` in the project root
* Edit the `.env` file and enter the required tokens

Start the xTuple Dashboard server

    vagrant $ dashing start

### xTuple Dashboard

Launch your local browser and navigate to application using localhost `http://localhost:3030`
or the static IP Address of the virtual machine `http://192.168.33.12:3030`
