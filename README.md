# Humio Single Node Setup

Installer for single node humio server.

## Installation

The Ansible script provided here is to setup single node humio server on **Ubuntu** platform. Ansible has to be installed on a control node and following command has to be executed to run the playbook which installs all pre-requisites required for humio i.e java, zookeeper and kafka and then installs humio software. The playbook uses `humio.java` role avaialble in ansible galaxy to install java.

```bash
ansible-playbook setup-humio.yml
```

## Role Variables

Role variables with default values are as below. These values can be overridden by initialising these variables with desired values in the `setup-humio.yml` playbook.
```
# role variable for humio.java role
java_version: 13.33.25-2 
redhat_java_version: 13.31.11-2

# role variables for dk.zookeeper role
zookeeper_version: 3.4.14
zookeeper_url: http://archive.apache.org/dist/zookeeper/zookeeper-{{ zookeeper_version }}/zookeeper-{{ zookeeper_version }}.tar.gz
zookeeper_data_dirs: /var/zookeeper/data

# role variables for dk.kafka role
kafka_scala_version: 2.13
kafka_version: 2.4.1
kafka_mirror: https://archive.apache.org/dist/kafka/
kafka_log_dirs: "/var/log/kafka"
kafka_data_dirs: "/var/kafka-data"

# role variables for dk.humio role
humio_mirror: https://repo.humio.com/repository/maven-public
humio_version: 1.20.1
humio_conf_dirs: /etc/humio
humio_filebeat_dirs: /etc/humio/filebeat
humio_work_dirs: /var/humio
humio_data_dirs: /var/humio/data
humio_log_dirs: /var/log/humio
humio_dirs: /opt/humio

```

## Example playbook

### Install Humio
An example `setup-humio.yml` playbook to install a single node humio server with default role variable values as a root user.

```yaml
- hosts: all
  remote_user: root
  become: true
  roles:
    - role: roles/humio.java    
    - role: roles/dk.zookeeper
    - role: roles/dk.kafka
    - role: roles/dk.humio

```
### Uninstall Humio
An example `remove-humio.yml` playbook is provided to uninstall humio, followed by kafa and zookeeper which were installed as part of the `setup-humio.yml` playbook. If role variables were customized during humio setup, those have to be provided during uninstallation as well.

