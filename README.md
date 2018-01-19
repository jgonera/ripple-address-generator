# Ripple Address Generator

Generate a new Ripple address (wallet) using the official ripple-lib as the
only dependency. The aim is to make this code as easy to audit as possible.

Print this document out or open on your phone because at some point you will
need to reboot your computer.

**Note:** Author takes no responsibility for any financial losses resulting
from using this guide and attached code.


## Step 1: Ubuntu USB stick

It's preferable to generate a new address on an operating system that is clean
and that can be destroyed just after creating the address. The operating system
you use day to day might contain all sorts of malicious software that you may
not be aware of (viruses, backdoors, keyloggers) and it's better to be safe
than sorry. We will create an Ubuntu bootable USB stick for this purpose.

Download Ubuntu 17.10.1 from the official website:
http://releases.ubuntu.com/17.10.1/ubuntu-17.10.1-desktop-amd64.iso

Then download SHA256SUMS to verify the integrity and authenticity of the Ubuntu
image you downloaded from the URL above:
* http://releases.ubuntu.com/17.10.1/SHA256SUMS
* http://releases.ubuntu.com/17.10.1/SHA256SUMS.gpg

If you are using Windows or macOS as your regular operating system you will
also need to download GPG from: https://gpgtools.org/

Follow this tutorial to verify your Ubuntu image download:
https://help.ubuntu.com/community/VerifyIsoHowto

After that download UNebootin for the operating system you are using daily
from: https://unetbootin.github.io/

Erase all data on the USB stick you are planning to use. Then launch UNetbootin
and use the `ubuntu-17.10.1-desktop-amd64.iso` to create a bootable USB stick.
Choose second option ("Diskimage") and click the "..." button. Then, choose the
`.iso` file of Ubuntu you downloaded earlier.


## Step 2: Generating a new address

Boot your computer using the USB stick created in step 1. When a blue
Unetbootin menu shows up, choose "Default" (just hit Enter).

After Ubuntu boots, connect to the Internet (WiFi or Ethernet). You can choose
the WiFi network by clicking on the arrow in the top right corner of the
screen. Then open the Terminal by clicking on "Activities" in the top left
corner and typing "Terminal" in the search field. In the terminal run the
following command to install Git:

```
sudo apt-get install git
```

Then run the following command to clone this repository:

```
git clone https://github.com/jgonera/ripple-address-generator.git
```

Then run the following commands to install all dependencies:

```
cd ripple-address-generator
bin/setup
```

Now **disconnect from the Internet** (turn WiFi off using the arrow in the top
right corner, unplug Ethernet) and run the following command:

```
bin/generate
```

Your address and associated secret will be printed out. Write them down on a
piece of paper or store in a secure (enrypted or offline) location. Use your
**address** to transfer the balance to.

Never disclose your **secret** and do not type it anywhere unless you want to
transfer the funds out of your wallet and you fully trust the software or
website you are using to transfer the funds out.

Run the following command to reboot your computer:

```
reboot
```

After rebooting, erase the contents of your USB stick (preferably by formatting
it).
