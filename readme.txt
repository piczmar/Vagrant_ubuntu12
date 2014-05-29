1. Install vagrant
2. Install virtualbox
3. Create Ubuntu 12 x32 image
	
	vagrant init
	vagrant box add hashicorp/precise32

4. add config in Vagrant file if it's not already there

	config.vm.box = "hashicorp/precise32"

5. Start VM

	vagrant up
	
6. Connect

	vagrant ssh
	 
7. Automation
http://docs.vagrantup.com/v2/getting-started/provisioning.html

	vagrant reload --provision
	
8. Networking
http://docs.vagrantup.com/v2/getting-started/networking.html
	
	vagrant reload
	
	then on host: http://127.0.0.1:4567
	
9. Make your image visible from anywhere
http://docs.vagrantup.com/v2/getting-started/share.html

	vagrant login
	vagrant share
	
10. Pause VM

	vagrant suspend

11. Resume

	vagrant up
	
12. Multiple machines
http://docs.vagrantup.com/v2/multi-machine/index.html

13. Snapshoting
http://priyaaank.tumblr.com/post/50707609769/snapshotting-vagrant

	vagrant plugin install vagrant-vbox-snapshot
	vagrant snapshot <vm name, e.g. default - same as in Vagrant file> <snapshot name>
	

Mongo DB
===========
1. Add to Vagrant config:
  config.vm.network :forwarded_port, host: 27018, guest: 27017

  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path ="../recipes"
    chef.add_recipe "git"
    chef.add_recipe "mongodb::10gen_repo"
    chef.add_recipe "vim"
    chef.add_recipe "curl"
    chef.add_recipe "apt"
    chef.add_recipe "build-essential"
  end

This is the Chef setup. All referenced recipes are located in the folder of the cookbooks_path. Note the mongodb::10gen_repo snippet, this is required to get the latest stable version and not the version that is supplied by the guest system you are using.

2. Add cookbooks in local project folder
$ mkdir cookbooks
$ cd cookbooks
$ git clone https://github.com/librato/nodejs-cookbook.git
$ git clone https://github.com/opscode-cookbooks/build-essential.git
$ git clone https://github.com/opscode-cookbooks/git.git
$ git clone https://github.com/opscode-cookbooks/apt.git

2. vagrant provision


References:
1. Nice presentation how to automate development & operations with Vagrant & Chef:
http://files.meetup.com/347566/Bmore_On_Rails_Chef.pdf

2. Provisioning MongoDB with Vagrant & Chef
http://stfnkhlr.de/2013/sep/6/using-chef-install-mongodb-vagrant-box/

3. Example MongoDB & NodeJs Cookbooks
https://github.com/tdegrunt/vagrant-chef-starter/tree/master/cookbooks/mongodb
http://workstuff.tumblr.com/post/50911984233/some-tips-on-getting-started-with-vagrant-and-chef

3. Managing multiple VMs with Vagrant
http://red-badger.com/blog/2013/02/21/automating-your-infrastructure-with-vagrant-chef-from-development-to-the-cloud/
