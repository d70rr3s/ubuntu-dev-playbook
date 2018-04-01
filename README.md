# Ubuntu web development machine
This playbook is designed to install my local development machine running Ubuntu and using Ansible.

## Requirements
  * Ansible 2.4+

## Running the playbook
You can run this playbook using a installer script (**recommended**) or manually.

### Installer script
  * Download the following [gist](https://gist.github.com/d70rr3s/2b4f2ab24cd1d5a5dac3bcf45274402e) an place it in your home folder.
  * Make sure that it can be executed `chmod ugo+x ~/launcher.sh`
  * Run it as root `sudo ~/launcher.sh`
  * Fill the prompts to configure the playbook execution.

### Manual
Clone or download this repository, edit the *default.config.yml* file and run the following command from the :
```bash
mkdir -p ~/.temp
ansible-galaxy install -r requirements.yml
ansible-playbook -i "localhost," -c local -K playbook.yml
```
Or, you can set the required vars directly in the command line:
```bash
mkdir -p ~/.temp
ansible-galaxy install -r requirements.yml
ansible-playbook -i "localhost," -c local -K playbook.yml --extra-vars "current_user=USERNAME git_fullname='YOUR_NAME' git_email='YOUR_EMAIL' installed_extras=[COMMA_DELIMITED_PACKAGES_NAMES]"
```
*__Note__: See *default.config.yml* file for var details and [read the docs](http://docs.ansible.com/playbooks_variables.html#passing-variables-on-the-command-line) for more information about passing vars through the command line*

## Packed software
### Development tools
This is the part when the overture plays in the background.
  * Languages:
    * PHP (7.0 by default but you may choose from 5.6 up to 7.2)
    * Java 8
    * NodeJS 6.x (see *Known issues*)
    * Ruby 2.x (see *Known issues*)
  * Virtualization:
    * Vagrant (comes with several plugins)
    * VirtualBox (5.2 latest stable release)
    * Docker
  * IDE & Editors:
    * ToolboxApp (Jetbrains central hub)
    * Sublime 3
    * Atom
    * Vim
  * VCS:
    * Git
    * Meld
  * Package managers:
    * Composer
    * Bower (legacy projects)
    * Yarn
    * Bundler
    * NPM

### End-user applications
Sidekick companions for the fellows from above.
  * NFS server (required when syncing files between host and guests machines).
  * IP table firewall (disabled by default)
  * Synapse
  * autojump
  * PuTTY
  * Filezilla
  * Terminator
  * Oh-my-ZSH
  * FZF
  * Google Chrome

## Supported distros
  * 17.10 Artful
  * 16.04 Xenial

## Known issues
I'll do something with this later.
  * NodeJS 5.x (maybe others) version [issue](https://github.com/geerlingguy/ansible-role-nodejs/issues/3), solution delete registered repositories.
  * Installing ruby may fail with latest role version as the gems are compiled in-situs see [this](https://github.com/geerlingguy/ansible-role-ruby/issues/33), solution reboot and re-run playbook or run it from tty.

## @TODO
  * ~~Detailed content list~~
  * Available vars and tweaks
  * Add more goodies

## Disclaimer
I stich up this playbook mostly using [Drupal VM](https://github.com/geerlingguy/drupal-vm.git) provitioning roles and tasks, thanks Jeff (@geerlingguy) and others for the terrific work you haved done building these roles.
