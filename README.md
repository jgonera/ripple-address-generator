# Ripple Address Generator

Generate a new Ripple address (wallet) using the official ripple-lib as the
only dependency. The aim is to make this code as easy to audit as possible.

Print this document out or open on your phone because at some point you will
need to reboot your computer.

**Note:** Author takes no responsibility for any financial losses resulting
from using this guide and attached code.


## Step 1: Ubuntu USB stick

It's preferable to generate a new address on an operating system that is clean
and that can be destroyed just after creating the address. We will create an
Ubuntu bootable USB stick for this purpose.

Download Ubuntu 17.10.1 from the official website:
http://releases.ubuntu.com/17.10.1/ubuntu-17.10.1-desktop-amd64.iso

Then download SHA256SUMS to verify the integrity and authenticity of the Ubuntu
image you downloaded from the URL above:
* http://releases.ubuntu.com/17.10.1/SHA256SUMS
* http://releases.ubuntu.com/17.10.1/SHA256SUMS.gpg

Follow this tutorial to verify sums:
https://help.ubuntu.com/community/VerifyIsoHowto

After that download UNebootin for the operating system you are using daily
from: https://unetbootin.github.io/

Erase all data on the USB stick you are planning to use. Then launch UNetbootin
and use the `ubuntu-17.10.1-desktop-amd64.iso` to create a bootable USB stick.


## Step 2: Generating a new address

Boot your computer using the USB stick created in step 1. TODO: instructions
for getting to live system.

After Ubuntu boots, connect to the Internet (WiFi or Ethernet) and open the
Terminal (TODO: how). Run the following command to clone this repository:

```
git clone https://github.com/jgonera/ripple-address-generator.git
```

Then run the following commands to install all dependencies:

```
cd ripple-address-generator
bin/setup
```

Now **disconnect from the Internet** (turn WiFi off, unplug Ethernet) and run
the following command:

```
bin/generate
```

Your address and associated secret will be printed out. Write them down on a
piece of paper or store in any secure (enrypted or offline) location.

Run the following command to reboot your computer:

```
reboot
```

After rebooting, erase the contents of your USB stick (preferably by formatting
it).
