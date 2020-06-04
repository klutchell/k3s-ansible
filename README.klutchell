# k3s-ansible

## install

```bash
# install ansible
sudo apt update
sudo apt install ansible

# clone k3s-ansible fork with ubuntu and nfs support
git clone https://github.com/klutchell/k3s-ansible.git
cd k3s-ansible

# copy inventory and configure hosts and group vars
cp -a inventory/* .
```

## init

```bash
# set new password on each new device
ssh ubuntu@192.168.8.5

# install ssh key on each new device
ssh-copy-id ubuntu@192.168.8.5

# run init to setup sudo and hostnames
ansible-playbook init.yml

# run site to create k3s master and nodes
ansible-playbook site.yml

# (if required) run reset to cleanup k3s master and nodes
ansible-playbook reset.yml
```

## nfs

```bash
# prepare DATA storage on k3s-master
ssh ubuntu@192.168.8.5
printf "g\nn\np\n1\n\n\nw\n" | sudo fdisk /dev/sda
sudo mkfs.ext4 /dev/sda1 -L DATA

# prepare CONFIG storage on k3s-master
ssh ubuntu@192.168.8.5
printf "g\nn\np\n1\n\n\nw\n" | sudo fdisk /dev/sdb
sudo mkfs.ext4 /dev/sdb1 -L CONFIG

# enable nfs server on master
ansible-playbook nfs-server.yml

# enable nfs clients on nodes
ansible-playbook nfs-clients.yml
```

## references

- <https://rancher.com/docs/k3s/latest/en/quick-start/>
- <https://www.digitalocean.com/community/curriculums/kubernetes-for-full-stack-developers>
- <https://opensource.com/article/20/3/kubernetes-raspberry-pi-k3s>
- <https://opensource.com/article/20/3/kubernetes-traefik>
- <https://opensource.com/article/20/3/ssl-letsencrypt-k3s>
- <https://github.com/zimmertr/Bootstrap-Kubernetes-with-QEMU>
- <https://kauri.io/install-raspbian-operating-system-and-prepare-the-system-for-kubernetes/7df2a9f9cf5f4f6eb217aa7223c01594/a>
- <https://advishnuprasad.com/blog/2016/03/29/setup-nfs-server-and-client-using-ansible/>
- <https://opensource.com/article/20/5/nfs-raspberry-pi>
- <https://github.com/kubernetes/examples/tree/master/staging/volumes/nfs>