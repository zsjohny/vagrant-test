# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.define "master" do |master|

      config.vm.provider :virtualbox do |vb|
          vb.customize ["modifyvm", :id, "--memory", "2048", "--cpus", "2"]
          vb.name = "master"
      end

      master.vm.box = "ubuntu/trusty64"
      master.vm.hostname = "master"
#      master.vm.network :forwarded_port, guest: 22 , host: 9601
      master.vm.network "private_network", ip: "172.168.1.20"

      master.vm.synced_folder "salt-master/", "/srv", type: "nfs"
      master.bindfs.bind_folder "/srv", \
                                "/srv", \
                                perms: "u=rwx:g=rwx:o=rx" , create_as_user: true

  end

  config.vm.define "web1" do |web1|

      config.vm.provider :virtualbox do |vb|
          vb.customize ["modifyvm", :id, "--memory", "2048", "--cpus", "2"]
          vb.name = "web1"
      end

      web1.vm.box = "ubuntu/trusty64"
      web1.vm.hostname = "web1"
#      web1.vm.network :forwarded_port, guest: 22 , host: 9602
      web1.vm.network "private_network", ip: "172.168.1.21"

      web1.vm.synced_folder "web1/", "/srv", type: "nfs"
      web1.bindfs.bind_folder "/srv", \
                               "/srv", \
                              perms: "u=rwx:g=rwx:o=rx" , create_as_user: true

  end

  config.vm.define "worker1" do |worker1|

      config.vm.provider :virtualbox do |vb|
          vb.customize ["modifyvm", :id, "--memory", "1024", "--cpus", "2"]
          vb.name = "worker1"
      end

     worker1.vm.box = "ubuntu/trusty64"
     worker1.vm.hostname = "worker1"
#     worker1.vm.network :forwarded_port, guest: 22 , host: 9603
     worker1.vm.network "private_network", ip: "172.168.1.22"

     worker1.vm.synced_folder "worker1/", "/srv", type: "nfs"
     worker1.bindfs.bind_folder "/srv", \
                               "/srv", \
                               perms: "u=rwx:g=rwx:o=rx" , create_as_user: true
  end

  config.vm.define "celery" do |celery|

      config.vm.provider :virtualbox do |vb|
          vb.customize ["modifyvm", :id, "--memory", "1024", "--cpus", "2"]
          vb.name = "celery"
      end

      celery.vm.box = "ubuntu/trusty64"
      celery.vm.hostname = "celery"
#     celery.vm.network :forwarded_port, guest: 22, host: 2202, disabled: true , id: "ssh"
#     celery.vm.network :forwarded_port, guest: 22, host: 9604,  auto_correct: true
      celery.vm.network "private_network", ip: "172.168.1.23"

      celery.vm.synced_folder "celery/", "/srv", type: "nfs"
      celery.bindfs.bind_folder "/srv", \
                            "/srv", \
                                perms: "u=rwx:g=rwx:o=rx" , create_as_user: true
  end

  config.vm.define "rmq" do |rmq|

      config.vm.provider :virtualbox do |vb|
          vb.customize ["modifyvm", :id, "--memory", "2048", "--cpus", "2"]
          vb.name = "rmq"
      end

      rmq.vm.box = "ubuntu/trusty64"
      rmq.vm.hostname = "rmq"
      rmq.vm.network "private_network", ip: "172.168.1.24"

      rmq.vm.synced_folder "rmq/", "/srv", type: "nfs"
      rmq.bindfs.bind_folder "/srv", \
                                "/srv", \
                                perms: "u=rwx:g=rwx:o=rx" , create_as_user: true

  end

  config.vm.define "varnish1" do |varnish1|

      config.vm.provider :virtualbox do |vb|
          vb.customize ["modifyvm", :id, "--memory", "1024", "--cpus", "2"]
          vb.name = "varnish1"
      end

      varnish1.vm.box = "ubuntu/trusty64"
      varnish1.vm.hostname = "varnish1"
      varnish1.vm.network "private_network", ip: "172.168.1.25"
      varnish1.vm.synced_folder "varnish1/", "/srv", type: "nfs"
      varnish1.bindfs.bind_folder "/srv", \
                                "/srv", \
                                perms: "u=rwx:g=rwx:o=rx" , create_as_user: true

  end

  config.vm.define "staging" do |staging|

      config.vm.provider :virtualbox do |vb|
          vb.customize ["modifyvm", :id, "--memory", "1024", "--cpus", "2"]
          vb.name = "staging"
      end

#      staging.vm.network "private_network", ip: "172.168.0.100",
#      bridge: 'en0: Wi-Fi (AirPort)'

      staging.vm.box = "ubuntu/trusty64"
      staging.vm.hostname = "staging"
      staging.vm.network "private_network", ip: "172.168.1.26"
      staging.vm.synced_folder "staging/", "/srv", type: "nfs"
      staging.bindfs.bind_folder "/srv", \
                                "/srv", \
                                perms: "u=rwx:g=rwx:o=rx" , create_as_user: true

  end
  config.vm.define "jenkins" do |jenkins|

      config.vm.provider :virtualbox do |vb|
          vb.customize ["modifyvm", :id, "--memory", "1024", "--cpus", "2"]
          vb.name = "jenkins"
      end

#      jenkins.vm.network "private_network", ip: "172.168.0.100",
#      bridge: 'en0: Wi-Fi (AirPort)'

      jenkins.vm.box = "ubuntu/trusty64"
      jenkins.vm.hostname = "jenkins"
      jenkins.vm.network "private_network", ip: "172.168.1.27"
      jenkins.vm.synced_folder "jenkins/", "/srv", type: "nfs"
      jenkins.bindfs.bind_folder "/srv", \
                                "/srv", \
                                perms: "u=rwx:g=rwx:o=rx" , create_as_user: true

  end
end
