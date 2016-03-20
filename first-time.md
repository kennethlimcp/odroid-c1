## 1st time boot up settings

### Odroid C1

#### Setup SSH without password

- Create a `.ssh` directory at the root directory
- copy the public key on your local machine over

```sh
$ cat ~/.ssh/id_rsa.pub | ssh odroid@xxxx.com 'mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys'
```

Note: if your local machine does not have a puclic/private key, you can use `ssh-keygen -t rsa` to generate one

- Test that it works and you can ssh into the remote box

```sh
$ ssh odroid@xxxx.com
```

You should see something like:

`Warning: Permanently added the ECDSA host key for IP address 'xxx.xxx.xxx.xxx' to the list of known hosts.`

- ssh to the board with username **odroid**

- Change password using `passwd odroid`

- Disable password login through ssh with:

```sh
$ sudo nano /etc/ssh/sshd_config
$ change to "PermitRootLogin no"
$ change to "PasswordAuthentication no" from "#PasswordAuthentication yes"
$ sudo service ssh restart

```

#### Miscellaneous
- Clear all the files in main directory:

```sh
$ cd ~
$ rm -rf *
```

- Resize root filesystem

Follow the instructions here: https://github.com/mdrjr/odroid-utility

Select `resize filesystem` once the utility launches

#### Setup Docker environment

Complete information and script from: https://github.com/umiddelb/z2d/

```sh
sudo apt-get -y install lxc aufs-tools cgroup-lite apparmor docker.io
sudo service docker stop
curl -sSL https://github.com/umiddelb/armhf/blob/master/bin/docker-1.9.1?raw=true | sudo dd of=/usr/bin/docker
sudo service docker start
sudo usermod -aG docker $SUDO_USER
```
