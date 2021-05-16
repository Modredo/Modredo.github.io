---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
---
# Posts

[Welcome post - sample ]({% post_url 2020-06-07-welcome-to-jekyll %})

# Raspberry Pi CCTV - motionEyeOS

## Brief 
I wanted to set up a simple, private, CCTV camera overlooking my blocks gated car parking area. This is due to increased activity to retail units downstairs and ... my bicycle being stolen. 
Idea is to only record when movement is detected and to store the files on my network storage: WD MyCloud. 

## Parts 

* Raspberry Pi 3B ( pretty sure any will work) 
    * SD card 
    * Power Supply 
* Camera 
* 5V Fan 
* Case

I have a 'Night Vision' raspberry pi compatible camera and a raspberry pi ( a couple but using Pi 3 B for testing). I have designed a simple case in Fusion 360 and printed it out. I will need to add a fan and ventilation slots to it along with figuring out best way of mounting it. Itertion is the key. 

## Installation 

Source:<br>
[github/motionEyeOS](https://github.com/ccrisan/motioneyeos)<br>
At author has great installation instructions please refer to them: <br>
[Installation Instruction](https://github.com/ccrisan/motioneyeos/wiki/Installation)<br>

I downloaded the image file as per instructions and extracted them with 'unxz'
```
sudo apt install xz-utils
unxz motioneyeos-raspberrypi3-20200606.img.xz
```
I have formated my SD card with 'Disks'</br>

![alt text](./img/disks.png "Disks")

And installed the image file to SD card passing through my WiFi data and assiging a fixed IP to the Pi: 

```
 ./writeimage.sh -d /dev/mmcblk0 -i "/home/krystian/Downloads/motioneyeos-raspberrypi3-20200606.img" -n 'WIFI_NAME:WIFI_Password' -s "192.168.1.101/24:192.168.1.1:8.8.8.8"
 ```

## Shared Storage 

This took me a little to long to get right and with the image installation are both a whole reason for recording this as a blog entry. I wanted to store the iamges and video from the camera on my Network Shared Drive, WD MyCloud. </br>
</br>
Using the server name would not work. As I did not know the IP of the disk I run nmap and got the IP. That IP then used as a server name was the key to get it working. 

So my config looked like this: 
```
Storage Device  : Network Share
Network Server  : 192.168.1.1
Share Name      : Krystian/CCTV
Share Username  : User 
Share Password  : Password 
Root Directory  : /
```

![alt text](./img/network_share.png "Disks")

## test areas
[About Page](./about.markdown)<br>
