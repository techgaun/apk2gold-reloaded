# Easy-as-pie Android Decompiler

This project is a fork of [apk2gold](https://github.com/lxdvs/apk2gold) which seems no longer maintained
to replace with recent version of apktool and better tooling with jadx.

## Updates

- apktool to 2.5.0 - [With Support for Android Pie](https://connortumbleson.com/2018/09/05/apktool-v2-3-4-released/).
- jadx 1.2.0 replacing dex2jar and jd-cmd

Original readme follows:

## Why

### One stop shop

Rather than using bunch of tools everytime, this tool allows you to invoke them in the right sequence
to produce all that's necessary for creating the decompiled version of APK

### Collocation of source files
Further, even after these steps were complete (usually a combination of dex2jar and JD-GUI),
I would be left with disparate sources of information; the decompiled Java would be over here in this directory,
while the un-DEXed content would be somewhere else (Really bad for importing into Eclipse!)

I basically wanted to make this generate a tree and source as close as possible to what the original Android developer sees.

## What

apk2gold is basically a small amount of original content (the R.* thing) and a script wrapping some excellent 3rd-party tools. It is designed to be easily installed and to get you the best results for Android app introspection as quickly as possible. The project stands on the shoulders of the following giants:

* **[skylot/jadx](https://github.com/skylot/jadx)**

* **[iBotPeaches/apktool](https://github.com/iBotPeaches/Apktool)**

## Installation

### Dependencies

You'll need git if you're going to clone. Also, java installed. git is only necessary for cloning the repo. You can also download [zip file](https://github.com/techgaun/apk2gold-reloaded/archive/master.zip) instead of cloning.

### Installing

```shell
git clone https://github.com/techgaun/apk2gold-reloaded $HOME/.apk2gold-reloaded
echo "export PATH=$PATH:$HOME/.apk2gold-reloaded" >> ~/.bashrc
source ~/.bashrc
```

now, you can run `apk2gold` command anywhere.

## Usage

### Getting the APK

There are different ways to acquire an APK, but the easiest is to just download it from the Play Store
and use ES File Explorer to back up the APK (ES File Explorer -> "AppMgr" tab -> long click on app you want -> backup).
The APK is now in the 'backups' directory on your SD card.
Now you can just USB it over (I like to email it to myself from ES File Explorer itself).
More depth can be found at [this SO post](http://stackoverflow.com/questions/12175904/where-can-i-find-the-apk-file-on-my-device-when-i-download-any-app-and-install).
There are several websites online that allow you to download APKs as well.

### Decompiling

The usage is very simple:

```shell
apk2gold <target>.apk
```

### Looking at the result

This will create a folder with the APK's name without '.apk' suffix. Everything is in there.
There is also an additional directory you may not recognize, `/.smali`,
which contains the Smali output from APKTool. Load it up in Eclipse and have fun!  
Note that the result will almost certainly not compile; that's not really the goal.
We just want to get an idea of whats happening in the source code, check for malicious shit, etc.
