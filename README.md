Fork 5minbootstrap ansible-driven for Debian 7 compatibility
=============

## Step 1: Set the root password

Run:

    yourmachine$ ssh root@server

Enter the initial root password from your hosting provider, then run:

	root@server# passwd


## Step 2: Fetch the bootstrap recipe

[https://github.com/fedir/5minbootstrap](https://github.com/fedir/5minbootstrap)

    yourmachine ~$ git clone https://github.com/fedir/5minbootstrap
	yourmachine ~$ cd 5minbootstrap


## Step 3: Edit hosts.ini

Ansible needs to know about the servers you want to manage.  There is
no fancy central database, just a text file with a list of
servers.  Oh, it's called an "inventory file."

Edit the `hosts.ini` that came with the repository.  Replace
`127.0.0.1` with your IP address, and `:2222` with your SSH port.

    [newservers]
	127.0.0.1:2222
	

## Step 4: Run the playbook

This is the needed invocation *for Vagrant*:

    yourmachine ~/5minbootstrap$ ansible-playbook -i hosts.ini bootstrap.yml --ask-pass --sudo
	
If you are logging into a fresh Linux server where you only have the `root` user, you need to run this command:

    yourmachine ~/5minbootstrap$ ansible-playbook -i hosts.ini bootstrap.yml --user root --ask-pass
	
## Step 6: Go get a cup of coffee because you're DONE.

I prefer hand-ground French pressed coffee myself.  Tea is also fine.


Ressources
==========
http://plusbryan.com/my-first-5-minutes-on-a-server-or-essential-security-for-linux-servers
http://practicalops.com/my-first-5-minutes-on-a-server.html
