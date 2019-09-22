# pi-gen-vagrant

This is sample vagrant machine to help to create SD-CARD images for raspberry pi using [this fork](https://github.com/6za/pi-gen) of `pi-gen`. 

> Original pi-gen available here: https://github.com/RPi-Distro/pi-gen



# Using 

On Host machine:
```bash 
git clone https://github.com/6za/pi-gen-vagrant.git
cd pi-gen-vagrant
vagrant up
vagrant ssh
```

On Vagrant machine:
- `YOUR_MANAGER_HOST_IP` is the machine used to manager cluster. A host ip is expected. 
```bash 
cd pi-gen/
echo "$YOUR_MANAGER_HOST_IP  raspi-manager" >> manager.host
sudo chmod 777 manager.host
CONTINUE=1 ./build-docker.sh
```
> Sometimes the image generation can fail in the process, just running it again seems to work most of the times. 

After a long while, you will have a image.

It would be something like `deploy/image_2019-09-21-RaspiDocker-lite.zip`

The best way to send the machine to a machine to burn it on a SD-card for your raspberry pi is to `scp` from this VM. 

```bash 
scp deploy/image_2019-09-21-RaspiDocker-lite.zip  $SOME_USER@$SOME_IP:~/Downloads/
```

Than on the hoster machine you can use [Etcher](https://www.balena.io/etcher/) to burt it the proper way in you SD-CARD. 
