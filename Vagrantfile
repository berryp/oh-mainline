# This configuration file is for Vagrant, a simple virtual
# machine manager. It requires VirtualBox to be installed
# and working.
#
# To learn more about Vagrant, visit:
# http://vagrantup.com/

Vagrant::Config.run do |config|
  # This virtual machine (VM) is created based off a tiny pre-configured
  # Debian VM. We'll call it squeeze, and we'll download it from
  # the creator's S3 URL, if necessary.
  config.vm.box = "lucid32"
  config.vm.box_url = "http://files.vagrantup.com/lucid32.box"

  # This is a workaround for an apparent bug in Vagrant, where sometimes it
  # fails to properly share the Puppet manifests with the VM.
  config.vm.share_folder("my-puppet-hack", "/tmp/vagrant-puppet", "puppet-provisioning-files")

  # Configure the VM so that it launches Puppet when it first runs.
  config.vm.provision :puppet do |puppet|
    puppet.manifests_path = "puppet-provisioning-files/manifests"
  end

  # Forward port 8000 into the VM
  # We use 8000 because it is the default port for Django,
  # so that is what all the documentation uses.
  config.vm.forward_port("web", 8000, 8000)

end

