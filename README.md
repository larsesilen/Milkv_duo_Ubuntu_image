# Milkv_duo_Ubuntu_image
This is an Ubuntu 22.04 image for milkv duo boards (256M and 512M)

This is an image for Ubuntu 22.04 for milk-v boards (risk-v). The starting point was the image found here: https://xyzdims.com/3d-printers/misc-hardware-notes/iot-milk-v-duo-risc-v-esbc-running-linux/
The image used seems to work on both the Milk-v duo 256m and on the Milk-v Duo S (512m). I used the Milk-v Duo S as the working platform because the processor has more memory available.

Using ordinary tools (apt) I installed the gcc compiler and other build essentials without problems.
Next I downloaded the Nano editor source code and successfully compiled the program that now is available as "nano" in the image.

The intention of this experiment is to get a low level development platform using milk-v duo 256m and the milk-v duo S 512m processors. 

The provided image can be flashed to a 64GiB SD card. It should be possible to shrink the root partition to flash the image to smaller cards. I didn't have suitable smaller cards available to test.

To make a working bootable SD card do:
Download the zipped image from: https://drive.google.com/file/d/1KVf03BGxgD8co9V2ADbmGR5E6TO2f0v-/view?usp=drive_link
On Linux 
gunzip Ubuntu_milkv_duo_S_512m.img.gz

The result is Ubuntu_milkv_duo_S_512m.img

Flash this to a 64GiB SD-card using for example the BalenaEtcher or the Linux "dd" command.

<h3>What have we got</h3>
The image provides a low level development environment using C, C++ and Python. 
The system can fairly easily be upgraded using Ubuntu CLI installation apt install xxxx .

Notice that this is a very simple preliminary experiment . There may be any number of incompatibilities in the image. So far it looks like CLI Ubuntu 22.04 works providing a software development environment that isn't dependent on the SDK.


