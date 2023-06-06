# Issues
For any issues, please open an issue or check if there's a solution already available in the issues section. Issues with solutions will be under closed issues. 

# macOS on ThinkPad X1 Carbon Gen 7
This repository is made to help run macOS on a ThinkPad X1 Carbon Gen 7.

This should help you get started on hackintoshing and any updates can be applied later. I may occasionally update this repo if I find the time but there's no guarantee.

I recommend going through the [Opencore install guide](https://dortania.github.io/OpenCore-Install-Guide/) once to fully understand everything that is going on here.

**NOTE**: macOS will not work with Samsung PM981/a drives out of the box. Suggest replacing or not using the drive with macOS.

Keep in mind that you have to generate your own serial numbers and ID's and stuff using [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) if you're doing a fresh install. Use your old ones from your old config.plist if you're just changing EFI's (TIP: Use MacBookPro15,4 but I've included that in the plist)

This hakcintosh will be complete only with [YogaSMC](https://github.com/zhen-zen/YogaSMC). After installing, please use the app and the system preferences add on as it enables some features for this to be complete.

**CAUTION**: Test drive this configuration once using a USB flash drive before you move it to the main EFI partition. I am not responsible for any damages incurred.

# Hardware Info

|**Component**|**Model**|
|:-|:-|
|**CPU**|Intel Core i7-8665u|
|**GPU**|Intel UHD Graphics 620|
|**RAM**|16GB 2400 MHz DDR4|
|**Storage**|512GB WD SN770 |
|**WiFi/Bluetooth**|Intel Wireless AC-9560 |
|**Touchpad**|Synaptics|
|**Display**| 14" WQHD |
|**Camera**| 720p HD w/ Privacy Shutter |
|**Battery**| Single 51 Wh |

# Screenshots
![Screenshot 2023-06-03 at 7 01 26 PM](https://github.com/Krissh-C/T490-macOS/assets/117280851/5fb19677-c076-4687-8bd6-cc688547fa91)

# What Works
- Keyboard (including all media keys)
- Trackpad and TrackPoint with clicky buttons
- Battery indicator
- Display Auto-Brightness
- HDMI
- Audio (Speakers, Headphone Jack, Bluetooth and USB-C headsets)
- Bluetooth
- Ethernet (Using Lenovo dongle)
- iCloud Services (iMessage, FaceTime, iCloud Drive)
- GPU Acceleration
- Camera
- External Microphone (⚠️ Internal Microphone does not work ⚠️)
- Sleep/Wake
- Trackpad with gestures
- CPU Power Management (suggest making your own using [CPUFriendFriend](https://github.com/corpnewt/CPUFriendFriend))
- Battery Indicator
- Handoff, Continuity
- AirPlay
- FileVault
- DRM Content
- Fan Control using [YogaSMC](https://github.com/zhen-zen/YogaSMC)
- Thunderbolt (Requires TB3 BIOS Assist to be on)
- All 4 speakers (see details below)
- Sidecar (Wired)

   ![Screenshot 2023-06-03 at 5 21 12 PM](https://github.com/Krissh-C/T490-macOS/assets/117280851/b3556d43-9213-4b42-976e-c0a73bce78b1)


# What doesn't work
- AirDrop
- Fingerprint Reader
- Sidecar (Wireless) + Universal Control (Airportitlwm limitation)

# Not Tested
- USB-C Video (audio works)

# Audio Setup
| Key       | Value    |
| --------- | -------- |
| boot-args | alcid=71 |

We are using the above boot-arg to initially setup your config.plist file. 

This will enable the top and bottom speakers in the **System Preferences --> Sound** allowing you to select either set of speakers. To combine the two you'll need to open **Audio MIDI Setup** (use Spotlight to find and open it) and create an **Aggregate Device** with both sets of speakers. Unfortunately you can't control the volume of an Aggregate Device with the volume keys. You'll need to install a utility as highlighted below.

Create **Multi-output device** or **Aggregate Device** in **Audio MIDI Setup** controller for all speakers - use utility like [AggregateVolumeMenu](https://github.com/adaskar/AggregateVolumeMenu) to control the volume

- See description here [Change Volume on Aggregate Sound](https://gurhanpolat.medium.com/change-volume-on-aggregate-sound-815fd575347a)

If you're happy with the setup above you can use the guide to replace alcid=71 per below:

- Add audio codec to DeviceProperties - layout-id | data | **47000000**

# Credits
- [Acidanthera](https://github.com/acidanthera)
- [Opencore install guide](https://dortania.github.io/OpenCore-Install-Guide/)
- [CorpNewt](https://github.com/corpnewt)
- [YogaSMC](https://github.com/zhen-zen/YogaSMC)
- [Aidanchandra's X1C7 Repo](https://github.com/aidanchandra/x1c7-hackintosh)
- [Seven-of-eleven's X1C7 Repo](https://github.com/seven-of-eleven/Lenovo-ThinkPad-X1C7-OC-Hackintosh)
- [Derived from my t490-macos repo](https://github.com/Krissh-C/T490-macOS)
