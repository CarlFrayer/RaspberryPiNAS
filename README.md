# Raspberry Pi NAS Project

### Introduction: 
 If you aren't familiar with what a NAS (Network Attached Storage) is, it's essentially a small computer that is hooked up to a storage drive or drives and acts as a file share on your network, allowing access to your files on any device. For this project I would like to give credit to this [guide](https://www.youtube.com/watch?v=gyOHTZvhnxY) by Michael Klements for inspiring me and being a good reference throughout the process.

Why did I need a NAS?  I observed a few issues inside of my workflow that the NAS would solve. Some of te issues i wnted to solve were;
   - The ability to update, and share files with multiple people without having to share via USB, email, or other mult-step file transfer option. 
   - Avoiding storing files on an already failing system hard drive.
   - Consolidating file storage to avoid users still using out of date files.
   - Inspiring collaboration on documents
 
### Choosing the NAS components.
 I originally had a 256GB USB plugged directly into an old router that I utilized solely for the purpose of file share. The reason I moved away from this is was because the router did not support higher versions of SMB, which inhibited modern Windows machines from attaching to it. Plus I wanted to dable into creating my own NAS and the OpenMediaVault operating system. Overall I wanted to keep the system cheap so you should see that reflect in the choices below. 

### **The Computer**
- I need something to act as a computer but I don't want the NAS to take up a ton of space. I decided to go with a Raspberry Pi Zero 2 W, This cost just $15 dollars and has the wireless feature indicated by the "W" in the name, as well as a quad core 64-bit processor that will beneficial to the project.

Raspberry Pi Zero 2 W - Credit: [Pi Cockpit](https://picockpit.com/raspberry-pi/everything-about-raspberry-pi-zero-2-w/)

  ![Pi Zero 2 W](https://i.imgur.com/WkT93OB.jpeg)

### **Storage**
- For storage an SSD was the obvious choice but I already had a small external Maxone 500GB Slim Portable HDD purchased for another project. I used this hard drive as well as a small 256GB PNY keychain USB that was already acting as the fileshare on the old router. For the RaspberryPi OS and main Pi Storage. I utilized the a [SanDisk 32GB MicroSD card](https://a.co/d/elCHsle) 

Maxone HDD - Credit: [Image from Amazon](https://a.co/d/9Xjghff)

![Maxone](https://imgur.com/HLHQLpA.jpg)

PNY USB SSD - Credit [Image from Amazon](https://a.co/d/7rDpArM)

![PNY](https://imgur.com/klTYsYR.jpg)

### Putting it all together
- I also purchased a Raspberry Pi Zero 2 W case kit off of Amazon to install the Pi into so I could mount it if needed and also provide it a little bit of protection, just in case.

iUniker Case - Credit [Image from Amazon](https://www.amazon.com/dp/B09XK36QNB?ref=ppx_yo2ov_dt_b_fed_asin_title)

 ![PiCase](https://imgur.com/Y8JZOas.jpg)

- Installing it inside the case was simple, removing a small plastic heat sink cover and four screws. After I installed it I cut a piece of velcro mounting tape and put it on the the back of the case to mount it to the Maxone HDD. Utilizing the wires that the kit came with I also had those routed so it looked relatively clean and didn't put any additional stress on the cables.
- With the included USB adapter I installed the external hard drive as well as the thumb drive, and the set up was now good to go. Now its on to flashing and the first boot.

### Flashing Pi and first boot
- Using the Micro SD card mentioned earlier I flashed it with Raspberry Pi OS Lite using the Raspberry Pi imager. I needed to change some settings so that we would be able to SSH into the Pi as well as have the Pi connect to the network wirelessly right away.

Raspberry Pi Imager - Credit [Image from google](https://assets.raspberrypi.com/static/4d26bd8bf3fa72e6c0c424f9aa7c32ea/dd4a0/imager.png)

![PiImager](https://imgur.com/wwn9kwe.png)

- After successfully flashing the MicroSD I was ready to install it into the Raspberry Pi. I installed it into the RaspberryPi and supplied power to the Pi and gave it about 5 minutes to fully boot up for the first time and get settled.
- After the 5 minutes were up it is now time to install the NAS software which is going to be OMV (Open Media Vault) in this case.

### Installing and Configuring the NAS Software - OMV
- To be able to install the software through SSH we will need the Raspberry Pi's IP address to connect into it. To do this we could check our router's DHCP table or use a utility like Angry IP scanner.
- Now that we have identified the IP we can ssh into it by entering the command
-  ```ssh pi@<Your IP>```
-  Getting into the pi we are going to update, and upgrade it with the following commands
 ``` sudo apt upgrade`
    sudo apt update```
- I let it sit for a few minutes waiting for the process to complete. After completion we are now ready to install OMV. We are able to do this through a script but be careful itilizing the one in the guide I used. It seemed to disable my wireless connection no matter what and to avoid that I had to use this script, which skips network setup
```
wget https://github.com/OpenMediaVault-Plugin-Developers/installScript/raw/master/install
chmod +x install
sudo ./install -n
```
- After running this script and confirming OMV has installed we can log in to OMV through the same IP but this time going through our browser.

From Here forward I followed OMV's recommendations and then customized it to fit my needs. If you would like to reference those steps you can follow this link: 
[OMV Guide](https://wiki.omv-extras.org/doku.php?id=omv7:new_user_guide)

### Summary
Raspberry Pi NAS is operational running OMV with 756GB of storage. 
Building the NAS was a fun and rewarding experience. It also opened my eyes up to the posibilites in regards to small computers being utilized for regular everyday tasks. OpenMediaVault was also fun to utilize and easy enough to get right into without any intimidation. I plan on doing some more Raspberry Pi projects in the future and it feels like the options are endless. Who knows what I will get into next? Remote cloud...
