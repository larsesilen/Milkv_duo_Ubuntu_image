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

Notice!
I didn't succeed in making a working version for the smallest 64MB milk-v duo 64m processor. Replacing the two files in the /boot partition with the corresponding files from the official Milk-v Linux version allows the image to 
boot almost to the end. It looks like the system tries to use an unimplemented kernal module and as a result (?) to mount some non existing directories:

[    1.376864] Kernel memory protection not selected by kernel config.<br>
[    1.383402] Run /sbin/init as init process<br>
[    1.387672]   with arguments:<br>
[    1.390772]     /sbin/init<br>
[    1.393602]   with environment:<br>
[    1.396850]     HOME=/<br>
[    1.399319]     TERM=linux<br>
[    1.402149] early_time_log: run_init_process: 6006201us<br>
[    1.455772] hub 1-1:1.0: USB hub found<br>
[    1.461127] hub 1-1:1.0: 4 ports detected<br>
[    1.902659] systemd[1]: System time before build time, advancing clock.<br>
[    1.933935] systemd[1]: Failed to look up module alias 'autofs4': Function not implemented<br>
[    1.948148] systemd[1]: Failed to mount tmpfs at /sys/fs/cgroup: No such file or directory<br>
[    1.958827] systemd[1]: Failed to mount cgroup at /sys/fs/cgroup/systemd: No such file or directory<br>
[!!!!!!] Failed to mount API filesystems.<br>
[    1.989410] systemd[1]: Freezing execution.<br>
[    3.165163] random: crng init done<br>

Comparing the boot of the smallest Milk-V duo 64m (using the CV1800B chipset) to the successful boots of the Milk-V duo 256m and also the Milk-V duo S (512m) seems to indicate that the small Milk-V duo 64 almost did it. Ideas are welcome. 
