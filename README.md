# Oosto v2 migration playbook to upgrade servers in Mendards environment

To be downloaded to the local Satellite machine which will have access to all the store servers.

Playbook needs to be run in two stages.

The first playbook backs up all v1 watchlist camera data (Not the application) to the /storage partition. Once the backup is completed all store machine will be updated to RHEL 7.9. Any store machine that is running RHEL workstation will be migrated over to RHEL server. Once the update to RHEL 7.9 is completed the playbook will prep and upgrade the stoe machine to RHEL 8 which is requred for Oosto v2


# oosto run install instructions

1. Download the repo to the node you wish to run the playbook from. # git clone https://github.com/paulwoodman/oosto_final.git

2. Edit the inventory file with the hosts you wish to run the playbook against.

3. Edit the main.yml file in the group_vars/all directory to suit the environment

4. Run the first playbook: ansible-playbook -i inventory rhel_upgrade.yml

5. Run the second playbook: ansible-playbook -i inventory oosto_upgrade.yml

6. SSH to the target machine to run the following commands to install Oosto v2

# ./ansible-dep-installer.sh
# ./run_playbook.sh -i inventory_inventory_update.ini install_k3s.yml -t airgap
