Vagrant.configure("2") do |config|
  config.vm.box = "rhel/7.2"
  config.vm.hostname = "satellite01"
  config.vm.synced_folder ".", "/vagrant", disabled: true

  # set vm resources for virtualbox
  config.vm.provider "virtualbox" do |v|
        v.memory = "4096"
        v.cpus = 2
        v.storage :file,
            :device => 'vdb',
            :size => '50G'
  end
  # set vm resources for libvirt
  config.vm.provider "libvirt" do |v|
        v.memory = 4096
        v.cpus = 2
        v.storage :file,
            :device => 'vdb',
            :size => '50G'
  end

  # work around to leave registration on ansible side
  if Vagrant.has_plugin?('vagrant-registration')
     config.registration.skip = true
  end

  # run ansible playbook to deploy satellite
  config.vm.provision :ansible do |ansible|
          ansible.playbook = "entrypoint.yml"
          ansible.sudo = true
  end
end
