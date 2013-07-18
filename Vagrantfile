# The environment variables TROVE_VM_SYNC_FOLDER_LOCATION can be set to
# change the directory where the trove, trove-integration, and
# python-troveclient are found.

# If you plan on making more available inside the VM than just what appears in
# /opt/stack (for example, if you have additional scripts you want to access
# to support particular OSes or configurations) you can change the source of
# the repos inside the VM from /trove to something nested under it (for example,
# trove/repos) by setting the environment variable TROVE_VM_OPT_STACK_SOURCE.

Vagrant.configure("2") do |config|
  config.vm.box = "openstack-trove"
  config.vm.box_url = "http://9e1a2926d405d51127ce-1dd7910aaf75de5d703b77f114f87ea9.r5.cf1.rackcdn.com/openstack-trove.box"

  vm_source = ENV['TROVE_VM_OPT_STACK_SOURCE'] or "../"
  config.vm.provision :shell, :path => "install-trove.sh", :args => vm_source

  config.vm.provider :vmware_fusion do |vmf|
    vmf.gui = "TRUE"
    vmf.vmx["memsize"] = 3072
  end

  location = ENV['TROVE_VM_SYNC_FOLDER_LOCATION'] or "../"
  config.vm.synced_folder location, "/trove/"

end
