# Ansible examples for Dell SONiC

[Collection repository](https://github.com/ansible-collections/dellemc.enterprise_sonic/tree/main)

### Environment setup

Run network automation Docker image with ansible collections installed:
```bash
docker run --rm -ti -v "$HOME/.ssh/id_ed25519:/id_ssh:ro" -v "$(pwd)/ansible-sonic-test:/runner" network-ee:2.2.2
```

Manual connection testing (assuming there is SSH public key in user's home directory):
```bash
$ ssh -i /id_ssh admin@10.113.0.13
```

### Ansible examples

```bash
# Connection credentials coming from inventory file
bash-5.1$ ansible -i inv.ini -m ping datacenter

# Explicitly specified connection credentials (SSH key-based authorization)
bash-5.1$ ansible -i 10.113.0.13, -m ping -u admin -e "ansible_private_key_file=/id_ssh" all

bash-5.1$ ansible-playbook sonic_system.ansible.yaml
```
