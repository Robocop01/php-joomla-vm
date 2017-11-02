Vagrant.configure(2) do |config|

    config.vm.define "joomla" do |joomla|
         # Base temmplate for virtualbox, we use debian 8.9.0 here
         #joomla.vm.box = "debian/jessie64"
         joomla.vm.box = "ubuntu/trusty64"
         # Domain on which our application will respond later on
         joomla.vm.hostname = "joomla.dev"
         # IP address will be used by the VM
         joomla.vm.network :private_network, ip: "192.168.5.2"
         joomla.vm.network :private_network, ip: "192.168.5.3"

         # Tell vagrant to run ansible as a provisioner
         joomla.vm.provision :ansible do |ansible|
             # where the playbook is located
             ansible.playbook = "provisioning/playbook.yml"
             # show the ansible-playbook command used by vagrant
             ansible.verbose = true
         end
     end

     # Access the shared vagrant directory via NFS, otherwise slow on mac and windows
     config.vm.synced_folder ".", "/vagrant", type: "nfs"

     config.vm.provider "virtualbox" do |v|
         # tell virtualbox to give our machine 1Gb RAM and 1 Cores
         v.memory = 1024
         v.cpus =1
     end
end
