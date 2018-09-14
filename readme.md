# Intro

Windows compatible built of [Vagrant](https://www.vagrantup.com/) centos/7 VM with included [ansible-container](https://www.ansible.com/integrations/containers/ansible-container) ([ansible-container on GitHub](https://github.com/ansible/ansible-container)).

# Description

This Vagrant file and [Ansible](https://www.ansible.com/) playbook creates a VM with a built-in ansible-container in a Python [virtualenv](https://virtualenv.pypa.io/en/stable/). The motivation was, that Ansible is not compatible with Windows, so the Ansible playbook must run on the VM. This is possible using 

```yaml
config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "playbook.yml"
end
```

Thus Ansible is not required. This vagrantfile playbook will install Ansible on the Vagrant VM, push the playbook to the VM and run the playbook.



# Prerequisits

* Install [Vagrant](https://www.vagrantup.com/).
* Edit the vagrantfile to define a mount from a local folder to a remote folder:
	```yaml
	config.vm.synced_folder "{{LOCAL FOLDER}}", "{{REMOTE FOLDER}}"
	```


# Preparing the VM

Run 

```vagrant up```

# How to run ansible-container

SSH to Vagrant VM

```vagrant ssh```

Cd to the Python virtualenv bin folder

```cd ansible-container-env/bin```

Activate virtualenv

```source activate```

Launch ansible-container example from a powershell.

```
PS C:\vagrant\centos7-vagrant-box> vagrant ssh
[vagrant@localhost ~]$ cd ansible-container-env/bin/
[vagrant@localhost bin]$ source activate
(ansible-container-env) [vagrant@localhost bin]$ ansible-container
usage: ansible-container [-h] [--debug] [--devel] [--engine ENGINE_NAME]
                         [--project-path BASE_PATH]
                         [--project-name PROJECT_NAME]
                         [--vars-files VARS_FILES] [--no-selinux]
                         [--config-file CONFIG_FILE]

                         {run,help,deploy,stop,destroy,restart,init,version,build,install,push,import}
                         ...
ansible-container: error: too few arguments
```