Vagrant LAMP
============

My default LAMP development stack configuration for Vagrant on debian 7.

Installation:
-------------

Install [vagrant](http://vagrantup.com/)

    $ gem install vagrant

Download and Install [VirtualBox](http://www.virtualbox.org/)

Download a vagrant box (name of the box is supposed to be debian-70)

    $ vagrant box add debian-70 https://static.nls.io/debian-70.box

Or get the box on its GitHub repo : [vagrant-debian-wheezy-box](https://github.com/gmoigneu/vagrant-debian-wheezy-box)

Clone this repository

Go to the repository folder and launch the box

    $ cd [repo]
    $ vagrant up

What's inside:
--------------

Installed software:

* Apache
* MySQL
* php
* phpMyAdmin
* Xdebug
* git, subversion
* mc, vim, screen, tmux, curl
* [MailCatcher](http://mailcatcher.me/)

Apache virtual hosts are created in your root folder or optionally in a per site configurable docroot and configured with data bag `sites`.

phpMyAdmin is available on every domain. For example:

* http://local.dev/phpmyadmin

PHP is configured to send mail via MailCatcher. Web frontend of MailCatcher is running on port 1080 and also available on every domain:

* http://local.dev:1080