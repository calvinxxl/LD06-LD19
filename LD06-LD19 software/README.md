

## English Version:

> This repositorise contains the SDK for LD19 DTOF radar.
>
> Basing on ROS, the SDK allows the development of LD19 on different platform(PC, SBC).

## General discription

The file structure of this repositories is shown in the graph below:

![file structure](./pic/文件结构.png)

You could find three directories: `datasheet`, `PC_ROS_SDK`, `SBC_ROS_SDK`.

In the `datasheet`, there're datasheet files of the radar LD19 in both English and Chinese.

The two versions of SDK are separately stored in `PC_ROS_SDK`and `SBC_ROS_SDK`, you have to **choose one version from the two** accroding to the next section. What's more, the detailed instructions are also in the two directories.

 Links are here:[PC_README](./PC_ROS_SDK/README_en.md),[SBC_README](./SBC_ROS_SDK/README_en.md)

## Difference betweent PC and SBC versions

**Please read this section with carefulness, the version of your choice could be decisive to the whole process.**

We use names "PC" and "SBC(Single Board Computer)" to indicate the features of the two versions, for the PC version was programmed to search the `CP2102` device, the functions of which are converting the UART signal to USB and simulating a virtual COM, while the SBC version will directly use the serial on the board.

Owing to the fact that most of PC do not have any Serial port, extra hardware(CP2102) is needed. On the contrary, SBCs like Raspberry Pi are equipped with Serial peripheral,  radar can be linked to the board through GPIOs.

For example, if you are going to connect your radar and Raspberry Pi through the USB port, then you need to use PC version rather than SBC version. 

If a inappropriate SDK is put into use, there won't be any abnormity but it just can't find the radar.

## Usage

1. Read the section above then choose the proper version for your hardware.
2. Please turn to the README contained in the directory of the version you chose for further instructions in detail.[PC_README](./PC_ROS_SDK/README_en.md),[SBC_README](./SBC_ROS_SDK/README_en.md)

## Notice

LD19 is basically the same as LD06 in all aspects, so some manual books are based on LD06, please be aware of the contents that need modifying.



