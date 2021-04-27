# -*- mode: ruby -*-
# vi: set ft=ruby :

require 'yaml'
require 'vagrant-aws'
Vagrant.configure('2') do |config|
    #config.vm.box = 'aws'
	config.vm.box = "ubuntu/trusty64"
	config.vm.network "forwarded_port", guest: 80, host: 8080	
    config.vm.provider 'aws' do |aws, override|
    aws.access_key_id = 'xxxxxxxxxxxxxxxxxxxxxxxxxxx'
    aws.secret_access_key = 'xxxxxxxxxxxxxxxxxxxxxxxxxx'
    aws.keypair_name = 'ssh-keypair-name'
    aws.instance_type = 't2.micro'
    aws.region = 'us-east-1'
    aws.ami = 'ami-20be7540'
    aws.security_groups = ['default']
    override.ssh.username = 'ubuntu'
    override.ssh.private_key_path = '~/.ssh/id_rsa.pub'
  end
  
  config.vm.provision :ansible do |ansible|
    ansible.playbook = "playbook.yml"
  end
  
end
