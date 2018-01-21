# Ripple Cold Wallet, the paranoid way

This guide describes how to generate a new Ripple wallet using the official
`ripple-lib` as the only dependency. The aim is to make this code as easy to
audit as possible and use only libraries offically released and documented by
Ripple.

A cold wallet is a wallet whose **secret** has never been exposed to the online
world and therefore, there is no possibility that a malicious software or a
malicious user intercepted it and will use it to steal your balance.

You do want to ensure this because with cryptocurrencies, contrary to what
we've been used to in banking, there is no authority that can help you prevent
fraud or refund fraudulent transactions. **If the funds are transferred out of
your account, it's final. You will not be able to regain them.**

Print this document out or open on your phone because at some point you will
need to reboot your computer.

**Note:** Author takes no responsibility for any financial losses resulting
from using this guide and attached code.


## Step 1: Ubuntu USB stick

It's crucial to generate a new wallet on an operating system that is clean
and that can be destroyed just after creating the wallet. The operating system
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

After that download UNebootin for the operating system you use daily from:
https://unetbootin.github.io/

Erase all data on the USB stick you are planning to use. Then launch UNetbootin
and use the `ubuntu-17.10.1-desktop-amd64.iso` to create a bootable USB stick.
Choose second option ("Diskimage") and click the "..." button. Then, choose the
`.iso` file of Ubuntu you downloaded earlier.


## Step 2: Generating a new wallet

Boot your computer using the USB stick created in step 1. When a blue
Unetbootin menu shows up, choose "Default" (just hit Enter).

After Ubuntu boots, open the Terminal by clicking on "Activities" in the top
left corner and typing "Terminal" in the search field. Then connect to the
Internet (WiFi or Ethernet). You can choose the WiFi network by clicking on the
arrow in the top right corner of the screen. If you're using a Mac and WiFi
doesn't work, see [Appendix: Fixing WiFi on
Macs](#appendix-fixing-wifi-on-macs).

In the terminal run the following command to install Git:

```
sudo apt-get install git
```

Then run the following command to clone this repository:

```
git clone https://github.com/jgonera/ripple-cold-wallet-paranoid.git
```

Then run the following commands to install all dependencies:

```
cd ripple-cold-wallet-paranoid
bin/setup
```

Now **disconnect from the Internet** (turn WiFi off using the arrow in the top
right corner, unplug Ethernet) and **don't ever connect back using your Ubuntu
USB stick**. Run the following command to generate a new wallet:

```
bin/generate
```

Your wallet address and associated secret will be displayed. Write them down
on a piece of paper or store in a secure (enrypted or offline) location. If you
want to use a printer, connect it directly to your computer (not through a
network) and make sure that the printer does not save the images of what it
prints in its internal memory.

Use your **address** to transfer the balance to. Never disclose your **secret**
and do not type it anywhere unless you want to transfer the funds out of your
wallet and you fully trust the software or website you are using to transfer
the funds out.

**Do not lose your address and secret.** If you lose them, you lose your funds,
period. Remember, there is no authority to help you regain control.

Run the following command to reboot your computer:

```
reboot
```

After rebooting, erase the contents of your USB stick (preferably by formatting
it with forced data erase). If you are very paranoid, physically destroy the
USB stick instead.


## Step 3: Funding a new wallet

The minimum balance for a wallet to become active (called Base Reserve) is
20 XRP. You can read about it here: https://ripple.com/build/reserves/

Since you most likely want to use your new cold wallet to safely store your
funds, I advise you to make two transfers to your new **address**:

1. Transfer 20 XRP to activate the wallet and verify that everything works
   (we're being paranoid). You can verify your balance at
   https://xrpcharts.ripple.com/#/graph by entering your **address** (NOT the
   **secret**!).
2. Transfer the rest of your funds (or as much as you want to securely store).


## Step 4: Keeping your wallet "cold"

**Remember**: Do not ever disclose your **secret**, unless you want to transfer
the funds to a different account. If you do that, you need to transfer all of
the balance out of your wallet because you can't be sure anymore that a
malicious user didn't intercept and store your secret (your wallet is no longer
"cold").

Assuming you had 1000 XRP in your wallet and you transferred 100 XRP to
someone, you should transfer 1000 - 100 = 900 XRP to a new cold wallet (simply
follow the process you just followed again).


## Appendix: Fixing WiFi on Macs

Run the following set of commands:

```
sudo sed --in-place=.old --expression='/cdrom:/!d' /etc/apt/sources.list
sudo apt-get install bcmwl-kernel-source
sudo mv /etc/apt/sources.list.old /etc/apt/sources.list
```

Now try connecting to WiFi again.
