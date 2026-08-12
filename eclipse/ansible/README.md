Ansible layout for IronSec-Labs pentest VM

Structure:
- inventory/: hosts definitions
- group_vars/: global variables
- roles/: role-based tasks (webapp, users)
- playbooks/: site.yml to run the lab
- ansible.cfg: project settings

Usage examples:

Run the site playbook against the local Vagrant VM (password-based root):

ANSIBLE_HOST_KEY_CHECKING=False ansible-playbook -i inventory/hosts.ini playbooks/site.yml -u root --ask-pass --extra-vars "ansible_port=2222"

Or use the vagrant private key (recommended):

vagrant ssh-config > /tmp/vagrant_ssh_config
# find IdentityFile from the config and then:
ANSIBLE_HOST_KEY_CHECKING=False ansible-playbook -i inventory/hosts.ini playbooks/site.yml -u vagrant --private-key=/path/to/IdentityFile --extra-vars "ansible_port=2222"
