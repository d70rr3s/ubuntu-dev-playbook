# Install my local (Ubuntu) machine

I use this playbook mostly cloned from [Drupal VM](https://github.com/geerlingguy/drupal-vm.git) provitioning roles and tasks, to install my local machine.

By default you cannot run playbooks to the host machine, to do so one must call ansible-playbook command as follows:

```bash
ansible-playbook -i "localhost," -c local -K playbook.yml
```

The *-K* option will prompt you for sudo password.

# @TODO
 * Detailed content list
 * Available vars and tweaks
 * Add more goodies

# Known issues
I'll do something with this later.

* NodeJS 5.x (maybe others) version [issue](https://github.com/geerlingguy/ansible-role-nodejs/issues/3), solution delete registered repositories