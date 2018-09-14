# Intro

Windows compatible built of Vagrant VM with included ansible-container.

# Description

This Vagrant file and Ansible playbook creates a VM with a built-in ansible-container in a Python virtualenv. The motivation was, that Ansible is not compatible with Windows, so the Ansible playbook must run on the VM. This is possible using 

```yaml
config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "playbook.yml"
end
```

Thus Ansible is not required. This vagrantfile playbook will push the playbook to the vagrant VM, install Ansible on the VM and run the playbook.

# Prerequisits

Install [Vagrant](https://www.vagrantup.com/).

# Preparing the VM

Run ```vagrant up```

# How to run ansible-container

SSH to Vagrant VM
```vagrant ssh```

Cd to the Python virtualenv bin folder
```cd ansible-container-env/bin```

Activate virtualenv
```source activate```

Launch ansible-container
```
usage: ansible-container [-h] [--debug] [--devel] [--engine ENGINE_NAME]
     [--project-path BASE_PATH]
     [--project-name PROJECT_NAME]
     [--vars-files VARS_FILES] [--no-selinux]
     [--config-file CONFIG_FILE]

     {run,help,deploy,stop,destroy,restart,init,version,build,install,push,import}
     ...
```