# Yocto

git clone git://git.yoctoproject.org/poky -b kirkstone

git clone https://git.yoctoproject.org/meta-raspberrypi/ -b kirkstone

source oe-init-build-env

local.conf file is used for user configuration and we are building the image for raspberry pi 4 then machine name should raspberrypi4 and comment other machine names in local.conf
You can set machine name based on your raspberry pi boards(meta-raspberrypi/conf/machine)

now, We have to add the meta-raspberrypi layer in the build/conf/bblayers.conf file. This file store information of all meta-layer path which used by the bitbake
In my case meta-raspberrypi layer path is /home/tutorialadda/yocto/poky/meta-raspberrypi

bitbake core-image-minimal

sudo bmaptool copy --bmap ${DIR}/poky/build/tmp/deploy/images/raspberrypi4/core-image-minimal-raspberrypi4.wic.bmap ${DIR}/poky/build/tmp/deploy/images/raspberrypi4/core-image-minimal-raspberrypi4.wic.bz2 /dev/sdd

add enable_uart=1 to config.txt
add console=ttyS0, 115200 to cmdline.txt


