
# HOW-TO setup Eclipse 2019.12 with latest ARM GNU Pluigins openOCD and xPacks

This guide will show you how you can setup eclipse 2019.12 with latest version of openOCD and help you to import an makefile project and start debugging (at least an STM32F4). It is not quite straight forward so I thought I write it down for myself and maybe it will be useful for others.
 Althought the screenshots are for windows the same commandline actions can also be made in linux (tested by myself)

## Get started
Almost all information is availalble at 
https://gnu-mcu-eclipse.github.io/
but it is somehow confusing to understand what you have to do if you have never done it before
Here i will try to show you how I got everything working

### The beginning
First open your browser and search in google for "gnu arm eclipse"
![google search](./images/google_search.png)
this is where your journey begins...

In the download section you can find the most links I have provided below but a bit more decentralised and I think they mixed up the old and new way of installing the plugins. But there is much more info on this site so it is worth to read some stuff there (QEMU seems to be very promicing). Also when something should be unclear from this guide you can try to figure out how it was meant in the original. 

Below i extracted all the steps with links which were necessary to install Eclipse in my Win10 PC

### Download Eclipse
Download eclipse but do not run it yet
https://github.com/gnu-mcu-eclipse/org.eclipse.epp.packages/releases/

To install the xPacks you will need XPM. XPM needs Node.js to be installed on your computer. If you got working XPM already then just skip this steps. 

#### Install Node.js
Go ahead and visit this link https://nodejs.org/en/ . download the exe and install it. It asked me if I would like to install addictional build tools os something like that and to be sure everything would work I did it
After that, if you type 
```
node --version
```
you should see something like this
![xpm install](./images/Unbenannt1.PNG)

Now with 
```
npm install --global xpm
```
you can install xpm.

### Install the ARM-Environment

*for linux: it is not necessary to run the commands as root or sudo, the xPacks will land in your home directory in linux under "/home/XXX/opt/xPacks" and in "C:\Users\XXX\AppData\Roaming\xPacks" on Windows*

### GNU MCU Eclipse Windows Build Tools
```
xpm install --global @gnu-mcu-eclipse/windows-build-tools@latest
```

### xPack GNU Arm Embedded GCC
```
xpm install --global @xpack-dev-tools/arm-none-eabi-gcc@latest
```
### xPack OpenOCD
```
xpm install --global @xpack-dev-tools/openocd@latest
```
It did everything in one commandline window and it looked like this
![xpm install](./images/Unbenannt4.PNG)

Now you can check if everything is working.
Start eclipse.

If you see something like this

![eclipse error](./images/Unbenannt6.PNG)

then you probably downloaded 64 Bit Version of eclipse but only have Java 32 Bit installed on your PC. 

If your Eclipse starts then you can skip this step

### Installing Java_x64

Visit 
https://www.java.com/en/download/manual.jsp
download and run installer. After that Eclipse should start

If you add the plugin updatesite to eclipse repos you will see that all the plugins are areday marked as installed because we did it already with the xpm packs (Unfortunately we installed ALL! plugins from this repo, even the ones we dont need for this particular project)

![eclipse error](./images/Unbenannt9.PNG)

So there is no need to install any plugins anymore.

### Install ARM MCU Packages

Click on Modules Button

![modules](./images/modules.png)

Sync with online database

![modules sync button](./images/modules_refresh.png)

You will see something like this

![module sync](./images/Unbenannt10.PNG)

This will take a while, you can make a break and drink coffee.
 I've got also some errors that some modules are not available. Just click on "Ignore all" and hope that it wasnt the module you needed for your development :)

If you get errors at the beginning like i did on linux, try to add another repository in 
```
Window->Preferences->C/C++->Packages->Repositories
```
Here is the link that worked for me
```
  http://sadevicepacksprodus.blob.core.windows.net/idxfile/index.pidx
```
 
project setup will follow in couple of days


to be continued......

 
