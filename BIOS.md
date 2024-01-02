## BIOS

The **BIOS**, stands for Basic Input/Output System , is a hardware dependent sofware, hosted in a flash memory (read only) that provides the primitive operations, necessery for the operating system to access the disckette drives and to interfare standar peripherals and test them in a process called **POST**("Power-On Self Test"). The **Bios** provides also devices capabilities (where memories are located and their size for example). This vision of separate code thats deals with the hardware makes the operating system portable.  

Early processors have a specefic adress were to start excecution, so by puting the bios in it the excecution of the bios starts. Systems with later processors provide logic to start running the BIOS from the system ROM.

In case of **cold boot**, the **Bios** start POST process. This process identifies, tests and initializes system devices such as the CPU, chipset, RAM, motherboard, video card, keyboard, mouse, hard disk drive, optical disc drive and other hardware, including integrated peripherals. This goals are achieved by sending a signal in each device bus in the motherBoard and wait for the response. all attached devices answers by sending their information. In this way the computer knows how much RAM you have, if there is present a keyboard or a mouse, which storage devices are available, screen resolution, etc ...  

See more about BIOS : https://en.wikipedia.org/wiki/BIOS

## BDOS

The **BDOS**, Basic Disk Operating System, this concept is introduced by **CP/M** machines.