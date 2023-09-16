Ansible Configuration File Generator
This Ansible project simplifies the generation of configuration files for a multi-node application cluster. It leverages Jinja2 templating to create customized configuration files based on the node's role, position in the cluster, and name.

Getting Started
Follow these steps to use this Ansible project for configuration file generation.

Prerequisites
Before you begin, ensure you have the following prerequisites installed on your system:

- Ansible (install with `pip install ansible`)
- Jinja2 (included with Ansible)
- Python 3

## Usage

1. Clone this repository:

git clone https://github.com/your-username/ansible-config-generator.git
cd ansible-config-generator

2. Define your cluster configuration in the group_vars/all.yml file. Here's an example:

all_nodes:
  node1:
    role: leader
    backup_for: ""
  node2:
    role: worker
  node3:
    role: worker
  node4:
    role: worker
  node5:
    role: backup
    backup_for: node1

Define each node by name and specify its role.
For backup nodes, specify which node they back up using the backup_for field.

3. Run the Ansible playbook to generate configuration files:

ansible-playbook -i inventory.ini playbook.yml

4. Retrieve the generated configuration files from the configs directory.

After running the command in step 3 configs directory will be created and configuration files will be generated in the configs directory.


# Configuration Directives
Common directives for all nodes:

cluster_name: "my_cluster"
log_level: "info"
Additional directives:

Leader: role: "leader"
Worker: role: "worker", worker_id: [unique_id]
Backup: role: "backup", backup_for: [node_name]
