###1st time boot up settings

#####Odroid C1

- ssh to the board with username **odroid**

- Change password using `passwd odroid`

- Clear all the files in main directory:

`rm -rf Desktop Documents Downloads Music Pictures Public Templates Videos`

- Resize root filesystem

Follow the instructions here: https://github.com/mdrjr/odroid-utility 

Select `resize filesystem` once the utility launches

- Setup Docker environment

`sudo apt-get install -y lxc aufs-tools cgroup-lite apparmor docker.io`

- Update Docker to 1.5.0 (as of 12 April 2015)

Download the binary here: `curl -O https://raw.githubusercontent.com/umiddelb/armhf/master/bin/docker-1.5.0 > docker-1.5.0`

Change file permission: `chmod a+x docker-1.5.0`

Stop docker: `sudo service docker.io stop`

Move the downloaded binary: `sudo mv docker-1.5.0 /usr/bin`

Replace the old binary with the new: `cd /usr/bin; sudo mv docker _docker; sudo ln -s docker-1.5.0 docker`

Fire up Docker!: `sudo service docker.io start`

