# vagrant-magento-2.16


Vagrantfile for latest magento (2.16) and latest Ubuntu (bento/ubuntu-14.04)

This is the Vagrantfile and Vagrantfile.config.yml adapted from the "Magento Developer Guide" book but updated based on the trial-and-errors with the latest magento, ubuntu and PHP

The objective is to address several issues with the original Vagrantfile provided by "Magento Developer Guide" so that it is compatible with the latest magento (current version 2.16) and Ubuntu (current version: Ubuntu 14.04.5 LTS)

Some known issues with the original Vagrantfile provided by "Magento Developer Guide" are:

* The vm.box "ubuntu/vivid64" for vagrant is not longer provided
* The default PHP version (7.1) provided by latest ubuntu (after running apt-get update on bento/ubuntu-14.04) is not compatible with magento 2.16 due to the issues with mcrypt no longer supported in PHP 7.1
* php5.6-mbstring and php5.6-zip are needed for the magento 2.16 to work correctly 

# Version

The following list the version of the various softwares installed by the Vagrantfile on the ubuntu VM:

* vm.box: bento/ubuntu-14.04
* magento: magento 2 (version: 2.16)
* PHP: 5.6
* MySQL: 5.6

Currently the Vagrantfile is tested to be working on host computer which is Windows 10

# Usage

* Install [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
* Install [Vagrant](https://www.vagrantup.com/downloads.html)
* Obtain the magento public and private secret keys (Follow this [link](http://devdocs.magento.com/guides/v2.1/install-gde/prereq/connect-auth.html)) and replace the "[magent_public_key]" and "[magento_private_key]" in Vagrantfile.config.yml with the obtained keys
* Obtain a github oauth access key (Follow this [link](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/) and replace the "[github_oauth]" in Vagrantfile.config.yml with the obtained github oauth token
* Change the "email@change.me" in Vagrantfile.config.yml to your email of choice
* Change the "[magento_host_path]" in Vagrantfile.config.yml to your local path on your host computer on which you want the magento files to be installed
* Run the following command on your host computer:

```bash
git clone https://github.com/chen0040/vagrant-magento-2.16.git
cd vagrant-magento-2.16
vagrant up
```

* Add the line "192.168.10.10 magento.box" to /etc/hosts on your host computer (If you host computer is Windows, then the hosts file is located at C:\Windows\System32\drivers\etc\hosts)
* Open your browser and enter "http://magento.box"


