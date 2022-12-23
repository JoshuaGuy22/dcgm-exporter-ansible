# dcgm-exporter-ansible
Quick and Dirty DCGM Ansible Playbook (Systemd Unit - No Container)

If your use case requires you to install [DCGM-Exporter](https://github.com/NVIDIA/dcgm-exporter) via ansible, but can't use docker, this is a VERY simple playbook on how to install it via Systemd.
This is written for Ubuntu 20.04. 

## What does it do?

This is a quick and dirty playbook for dcgm-exporter. There are a million ways to improve it, but this will get you going if you're in a pinch.
I followed the 'MakeFile' from source steps [here](https://github.com/NVIDIA/dcgm-exporter/tree/main#building-from-source) to create the binary. I would reccommend that you create your own to ensure the latest version of DCGM-Exporter. 

The playbook simply installs the required packages provided by NVIDIA's repositories, and creates a systemd unit for the binary. After the playbooks runs, you should have a running dcgm_exporter.service exposing port 9400 with GPU metrics. Have fun scraping! 

## Running the playbook

_This is a simplified method of running it from your host, I would reccommend that you tie it to your env using inventory host files, pipelines, etc_.

```bash
# dry-run the playbook
ansible-playbook -i localhost, dcgm-exporter/dcgm_exporter.yml -vv --check

# apply the playbook
ansible-playbook -i localhost, dcgm-exporter/dcgm_exporter.yml -vv
```
