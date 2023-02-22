---
title: The Ultimate Windows Install
date: 2023-02-22 18:00:00 +0100
categories: [windows, debloat]
tags: [windows, windows 10, windows 11, debloat]
---

Windows is pretty bloated. Who needs the Microsoft Maps, Cortana, Groove Music, Get Help, Candy Crush, Roblox or whoever is paying them the most at the time? ***Nobody.***

This guide will show you how to install Windows 10 (or Windows 11!), removing the bloatware, debloating and creating a faster OS.

# Credits

This would not be possible without this amazing script from Chris Titus Tech

[GitHub: ChrisTitusTech/winutil](https://github.com/ChrisTitusTech/winutil)

[YouTube: Chris Titus Tech](https://www.youtube.com/@ChrisTitusTech)

[CTT Website](https://christitus.com/)

You should not blindly trust random scripts, so I recommend that you look through the script before running it. (GitHub link)

# Windows Install

Windows installation is pretty easy now, and is just which drive you would like to install, and what version.

![windows-install-01](/assets/img/2023-02-22-the-ultimate-windows-install/windows-install-screen-01.png)



The problem is once you reach the OOBE (Out Of Box Experience) which will ***force*** you into using a Microsoft Account most of the time.

![microsoft-account-oobe](/assets/img/2023-02-22-the-ultimate-windows-install/microsoft-account-oobe.png)

However, there are ways to easily bypass this such as:

- Disabling/Unplugging network interfaces/connections (From Windows 11 22H2 and onwards a bypass requires you to also open CMD using Shift + F10, typing **OOBE\BYPASSNRO** to bypass the "Let's connect you to a network" screen. This will allow you to create a Local user account)
- Use a banned e-mail address (such as **no@thankyou.com** and then typing any random password on the next screen. It will then display a "Oops, something went wrong" screen, allowing you to create a Local user account.) [Source](https://www.neowin.net/news/bypass-microsoft-account-requirement-when-setting-up-windows-11-with-internet/)

## Microsoft Security Questions for Local Accounts

Microsoft also requires you to give you security questions for accounts if you setup your password in the OOBE (Out Of Box Experience). 

![microsoft-security-questions-oobe](/assets/img/2023-02-22-the-ultimate-windows-install/microsoft-security-questions-oobe.png)

The solution to bypassing this is to ***not*** set a password while inside of OOBE (Out Of Box Experience)

This will then ***not*** ask you for any security questions, allowing you to continue the installation.

## Microsoft "Services"

Microsoft asks for "your permission" at the end of OOBE (Out Of Box Experience) and wants data such as your location, diagnostic data, "inking & typing" (their special way of wording a keylogger!), and a "tailored experience" (more data for advertising) and an advertising ID.

![microsoft-services-lies](/assets/img/2023-02-22-the-ultimate-windows-install/microsoft-services-lies.png)

This is not something you can bypass with the stock Windows ISO, but selecting the least data to send to Microsoft is the best (even if they will likely still use more data anyway) as the rest can be removed later in the "Scripts" section.

## Cortana! Everyone's favourite assistant (or so Microsoft thinks)

![microsoft-cortana-oobe-01](/assets/img/2023-02-22-the-ultimate-windows-install/microsoft-cortana-oobe-01.png)

Microsoft, at least in Windows 10 believes that Cortana can do everything and should do everything for you.

Declining these should do everything, and anything remaining can be removed later.

(Oddly, Microsoft removed Cortana in Windows 11... I wonder why)

## We're getting everything ready for you

![microsoft-oobe-getting-everything-ready-for-you](/assets/img/2023-02-22-the-ultimate-windows-install/microsoft-oobe-getting-everything-ready-for-you.png)

After finishing all of the OOBE (Out Of Box Experience) questions, you will now see this slighly sinister screen suggesting you no longer have any "control". Windows at this point will attempt to install any more bloatware until your system cannot handle it anymore.

To escape out of this, you can just run CTRL + ALT + DEL and click "Sign out".

![microsoft-oobe-getting-everything-ready-ctrl-alt-del](/assets/img/2023-02-22-the-ultimate-windows-install/microsoft-oobe-getting-everything-ready-ctrl-alt-del.png)

You should now be able to see your typical Windows login screen at this point.

![windows-login-screen](/assets/img/2023-02-22-the-ultimate-windows-install/windows-login-screen.png)

Click "Sign in"!

![fresh-install-desktop-no-config](/assets/img/2023-02-22-the-ultimate-windows-install/fresh-install-desktop-no-config.png)

You will now be able to see your standard Windows 10 desktop. You can now connect to the internet, set a password or anything else you would like to do before debloating or installing applications. (such as installing drivers!)

# The debloat process

This is the point where you will now start debloating windowss

Here is a list of the tools you will use (Links are updated as of 22 February 2023):

- Chris Titus Winutil (Debloat script + Installation)

Yep. That's it. One singular script.

To start, open a Powershell as admin. This can be done by right-clicking the start menu and clicking "Windows Powershell (Admin)". 

You will now be greeted with a Powershell window. You can run the script by inputting this:

```powershell
iwr -useb https://christitus.com/win | iex
```

Or an even shorter one (may not always work):

```powershell
irm christitus.com/win | iex
```

After pressing enter, you will now be presented to this window.

![ctt-script-overview](/assets/img/2023-02-22-the-ultimate-windows-install/ctt-script-overview.png)

## Overview

Within this window, you will see there are 4 menus - Install, Tweaks, Config, Updates.

Let's go through what each one has, and allows you to do.

### Install Window

![ctt-script-overview](/assets/img/2023-02-22-the-ultimate-windows-install/ctt-script-overview.png)

The install window contains a list of web browsers, development applications, games, applications, multimedia tools and utilities. This mainly uses winget tool, which is similar to a unix-like package manager. An example of this is 

```powershell 
winget install -e --id Mozilla.Firefox
```

(If you want to look further, here's a very nice site directory site to make winget packages simpler: [winget.run](https://winget.run))

### Tweaks window

![ctt-script-tweaks](/assets/img/2023-02-22-the-ultimate-windows-install/ctt-script-tweaks.png)

The tweaks window contains tweaks that are pretty much essential. I typically will enable most of them under "Essential Tweaks" and some under "Misc. Tweaks". 

### Config window

![ctt-script-config](/assets/img/2023-02-22-the-ultimate-windows-install/ctt-script-config.png)

The config window includes easy installation for useful windows features (some now hidden normally!) and allows you to check for system corruption as well. It also has easy to click buttons with access to the classic Control Panel menus instead of the terrible newer Windows Settings app.

![ctt-script-updates](/assets/img/2023-02-22-the-ultimate-windows-install/ctt-script-updates.png)

The updates window, as the name entails includes settings for updating. This is pretty easy to understand and typically I use the "Security Settings". This includes:

- Delays feature updates by 2 years
- Delays security updates by 4 days (This may seem odd, but it is if they are flawed security patches at first release)

Install all the application, tweak your settings and follow through everything. Once you are ready, close the Powershell window and restart.

## Cleaning up

You now have a debloated windows install, and will only have the Microsoft bloatware apps left to remove, clean up the start menu and anything else you would like to do.

Here is a list of the apps I would classify as Microsoft bloatware.

- 3D Viewer
- Alarms & Clock
- Feedback Hub
- Films & TV
- Get Help
- Groove Music
- Mail
- Maps
- Microsoft Solitaire Collection
- Mixed Reality Portal
- Office (Not actual office, it's a link to web version)
- OneDrive (Optional, but IMO it uses too much resources)
- OneNote
- Paint 3D
- People
- Skype
- Snip & Sketch
- Sticky Notes
- Tips
- Voice Recorder
- Weather
- Xbox
- Xbox Game Bar
- Your Phone

Wow. That is a lot. Let's remove them.

Some of these can be removed through normal windows tools, so this will be done after.

To remove these we will go through them one-by-one. Start by opening a Powershell (Admin) window.

Run these commands for each one you want to remove.

Alarms & Clock:

```powershell
get-appxpackage *Microsoft.WindowsAlarms* | remove-appxpackage
```

Films & TV:

```powershell
get-appxpackage Microsoft.ZuneVideo | remove-appxpackage
```

Get Help:

```powershell
get-appxpackage *Microsoft.GetHelp* | remove-appxpackge
```

Maps:

```powershell
get-appxpackage *Maps* | remove-appxpackage
```

Paint 3D:

```powershell
get-appxpackage Microsoft.MSPaint | remove-appxpackage
```

Paint 3D may also require removing the "Edit with Paint 3D" button from the context menu.

This can be done by editing the registry.

**Important**: Editing the registry can cause problems. Create a backup, or restore point and take care.

Use the Windows key + R shortcut to open the Run command.

Type `regedit` and click OK.

Browse to `HKEY_LOCAL_MACHINE\SOFTWARE\Classes\SystemFileAssociations\.jpeg\Shell`

Right click the `3D Edit` (folder) key. Click Delete. 

The context menu will not reappear after reinstallation of Paint 3D, so you will need to restore the entry in the future.

People:
```powershell
get-appxpackage *People* | remove-appxpackage
```

Xbox Game Bar:

```powershell
get-appxpackage *xbox* | remove-appxpackage
```

Your Phone:

```powershell
get-appxpackage Microsoft.YourPhone | remove-appxpackage
```

The rest of these can be uninstalled using the windows settings app, or some of them using `appwiz.cpl`.

You can now customize the taskbar by right clicking on icons, and the taskbar to remove items such as the Search bar.

You can further customize the start button by removing the bloatware advertisements for apps.

![start-menu-fresh](/assets/img/2023-02-22-the-ultimate-windows-install/start-menu-fresh.png)

I personally also like to remove items further by searching for "Turn system icons on or off", and "Select which icons appear on the taskbar"

At this point, I typically will remove all desktop icons and change the wallpaper.

You can also activate Windows through whatever means available to you.

You should now have a debloated Windows install. You can also install O&O shut up for even more tweaking of your system.

It is recommended to create a system snapshot at this point to revert to, or before any updates as Microsoft may attempt to un-tweak your system, forcing you to follow through this guide again.

If there are any further tweaks or any issues, leave them under my GitHub issues [here](https://github.com/msinfo32github/msinfo32github.github.io/issues/)