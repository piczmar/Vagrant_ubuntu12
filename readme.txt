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
	
References:
1. Nice presentation how to automate development & operations with Vagrant & Chef:
http://files.meetup.com/347566/Bmore_On_Rails_Chef.pdf

