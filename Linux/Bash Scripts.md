## Bash Commands

### Create the following directories to place the playbooks and configuration files for filebeat and metricbeat
mkdir /etc/ansible/roles
mkdir /etc/ansible/roles/files

### Pull the yaml playbooks from this commit and place them in the newly created direcory 'roles'
curl https://raw.githubusercontent.com/aamerian20/Project-ELK-stack/main/Ansible/1.Setup_DVWA.txt > /etc/ansible/roles/setup_DVWA.yml
curl https://raw.githubusercontent.com/aamerian20/Project-ELK-stack/main/Ansible/2.Install_Elk.yml.txt > /etc/ansible/roles/install_elk.yml
curl https://raw.githubusercontent.com/aamerian20/Project-ELK-stack/main/Ansible/3.Filebeat_Playbook.yml.txt > /etc/ansible/roles/filebeat_playbook.yml
curl https://raw.githubusercontent.com/aamerian20/Project-ELK-stack/main/Ansible/4.metricbeat_playbook.yml.txt > /etc/ansible/roles/metricbeat_playbook.yml


### Run the yaml playbook in the following order to install and configure the DVWA, ELK VM, filebeat, and metricbeat
ansible-playbook /etc/ansible/roles/setup_DVWA.yml
ansible-playbook /etc/ansible/roles/install_elk.yml
ansible-playbook /etc/ansible/roles/filebeat_playbook.yml
ansible-playbook /etc/ansible/roles/metricbeat_playbook.yml

You're done! 
Navigate to the IP addresses of your DVWA and ELK VM to test if it works.