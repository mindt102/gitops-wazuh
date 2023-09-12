# Integrate Wazuh with GitOps.

## Description
This is a Git repository to automate the integration of Wazuh with Ansible and GitLab CI/CD to deploy Wazuh server and agents.

## Stages
- `wazuhserver`: Deploy wazuh indexer, dashboard, and manager on the target server
- `wazuhagents`: Deploy wazuh agent on the target servers

## Usage
Upload the content of this repository to a GitLab project and create the following secret variables:
- `ANSIBLE_CFG`: (type: File) is the content of the Ansible configuration file. Example:
    ```
    [defaults]
    remote_user = vagrant
    host_key_checking = False
    ```
    - `remote_user` specify the user ansible will use to access the target machines. The target machines should be preconfigured with the public ssh key for this user.
    - `host_key_checking` is set to false to ignore prompt for known hosts

- `ANSIBLE_INVENTORY`: (type: File) is the content of the Ansible inventory file. This file should be stored as a secret variable in the GitLab project. Example:
    ```
    [wazuh-agents]
    10.0.0.11
    10.0.0.12

    [wazuh-server]
    10.0.0.13
    ```