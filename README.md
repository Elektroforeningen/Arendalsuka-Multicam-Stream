# Arendalsuka-Multicam-Stream
This repository is both a "how to" and documentation for how The Electrical Association in Norway set up their live streams during Arendalsuka 2024 for both Facebook and LinkedIn with multiple Logitech MEVO cameras and RØDE microphones. This solution uses RTMP to avoid recent issues with the Mevo Multicam App. This solution was used without issues for 6 live streams across 5 days and the recordings are available on YouTube: [Efo - Elektroforeningen channel on YouTube](https://www.youtube.com/@efo-elektroforeningen9052/videos)

All software used is freeware or the "free" version of the app, except for Restream.io which is a paid service that handles streaming to multiple destinations like Facebook and LinkedIn.
You can use the free version of Restream.io, but you'll get a "Restream" watermark on your video. There are alternatives to Restream.io but we have not tried anything else (yet).

We did try using NDI and SRT but that resulted in issues with lag, disconnections and audio which was not in sync with the video.
Using RTMP between an iPad with the MEVO Multicam app and an Windows laptop with OBS (Open Broadcaster Software) solved the issues we had.

# Table of contents:
* [tl;dr -guide (Windows)](https://github.com/Elektroforeningen/Arendalsuka-Multicam-Stream/edit/main/README.md#tldr--guide-windows)
  * [Configure stream key for MonaTiny](https://github.com/Elektroforeningen/Arendalsuka-Multicam-Stream/edit/main/README.md#configure-stream-key-for-monatiny) 
* [Requirements that were given which resulted in this solution](https://github.com/Elektroforeningen/Arendalsuka-Multicam-Stream/edit/main/README.md#requirements-that-were-given-which-resulted-in-this-solution)
* [Hardware](https://github.com/Elektroforeningen/Arendalsuka-Multicam-Stream/edit/main/README.md#hardware)
* [Hardware diagram](https://github.com/Elektroforeningen/Arendalsuka-Multicam-Stream/edit/main/README.md#hardware-diagram)
* [Software](https://github.com/Elektroforeningen/Arendalsuka-Multicam-Stream/edit/main/README.md#software)
  * [If you have a Mac and not a Windows/Linux pc](https://github.com/Elektroforeningen/Arendalsuka-Multicam-Stream/edit/main/README.md#if-you-have-a-mac-and-not-a-windowslinux-pc)

# tl;dr -guide (Windows)

If you just need the bare minimum for connecting the MEVO cameras to OBS using RTMP:

* Connect the MEVO cameras to the MEVO Multicam app on your iPad (or iPhone, or Android device)
* Start MonaTiny on your windows pc, it should look something like the screenshot below:
  * (if you have not configured MonaTiny with a key yet read [Configure stream key for MonaTiny:](https://github.com/Elektroforeningen/Arendalsuka-Multicam-Stream/edit/main/README.md#configure-stream-key-for-monatiny) first)

  ![Screenshot_758](https://github.com/user-attachments/assets/bc34efcc-dd7f-4502-9ccc-1d054a076e76)

* Check that the IPv4 -address has not changed since last time using `ipconfig` in cmd/terminal on the windows pc, see example below:

  ![Screenshot_757](https://github.com/user-attachments/assets/2eac4de3-f224-4535-b8e1-b859dd48d0ee)

* In the MEVO Multicam -app on the iPad, use the address `rtmp://(your IP)/live/` and the key `abc` (if you picked the stream key `abc`) as RTMP output/destination and start streaming
* Open OBS on the windows pc and add a new `Media Source` with the address `rtmp://(your IP):1935/live/abc`

  ![Screenshot_756](https://github.com/user-attachments/assets/a35f4b74-8515-4c75-be9d-00dfe4f5b677)
  
* You should now see the MEVO camera in OBS and you can stream to whatever you want from OBS

## Configure stream key for MonaTiny

* Run MonaTiny at least once so that it creates the folder `www`
  * Before:

  ![Screenshot_759](https://github.com/user-attachments/assets/36f8bc93-d464-423f-a4dc-8acddbffd8f5)
  * After:

  ![Screenshot_760](https://github.com/user-attachments/assets/5a9d3811-6040-4545-8752-0a0b17d92951)
* Close MonaTiny
* Create a new folder in the folder `www` with the stream key of your choice, for example `abc`

  ![Screenshot_762](https://github.com/user-attachments/assets/98a3f909-c0cb-4c1d-ac99-46efbedaad54)
* Run MonaTiny again

## Requirements that were given which resulted in this solution

* Must have 3 camera angles
* Must have 2 microphones
* The Video and Audio must be in sync on the live stream
* Must have 1 speaker for the audience at location with 0 latency/delay
* The live stream should be on Facebook and LinkedIn at the same time

Because the video and audio must be in sync on the live stream, and the speaker for the audience at location must also be in sync, it was decided to split the audio output from the RØDE microphone receiver using a 3.5mm minijack splitter to 1 of the 3 MEVO start cameras and the speaker.

# Hardware

* [MEVO start camera 3-Pack](https://www.mevo.com/no-NO/products/mevo-start-3-pack)
* Windows 11 laptop
* iPad
* 5G Wi-Fi router
* [RØDE Wireless GO II](https://rode.com/en/microphones/wireless/wirelessgoii?variant_sku=WIGOII) (2 microphones 1 receiver)
* [Bose S1 Pro speaker](https://support.bose.com/s/product/s1-pro-portable-bluetooth-speaker-system/01t8c00000OydMeAAJ?language=en_US) (for the audience at location)
* 3.5mm minijack splitter
* 3.5mm cables
* [Apple USB C Digital AV multiport adapter](https://www.apple.com/shop/product/MW5M3AM/A/usb-c-digital-av-multiport-adapter)

# Hardware diagram

Diagram of the hardware-setup used, made using [https://draw.io/](https://draw.io/)

![Arendalsuka-Multicam-Stream.png](Arendalsuka-Multicam-Stream.png)

# Software

The MEVO cameras are connected to the iPad using the [Logitech Mevo Multicam App](https://apps.apple.com/us/app/logitech-mevo-multicam/id1503021034) (free version).

The RØDE Receiver is set up using the [RØDE Central Mobile App](https://apps.apple.com/us/app/r%C3%B8de-central-mobile/id1576314986) (free app).

The laptop is receiving the RTMP stream from the Mevo Multicam app on the iPad using [MonaServer (MonaTiny version)](https://sourceforge.net/projects/monaserver/) (freeware, GPL-3.0 license)

The setup for MonaServer/MonaTiny is from the thread [How do I turn my PC into a local RTMP server? So Mevo can broadcast to it locally](https://www.reddit.com/r/mevocamera/comments/bd5182/how_do_i_turn_my_pc_into_a_local_rtmp_server_so/) on the subreddit [r/mevocamera](https://www.reddit.com/r/mevocamera/) by Reddit-user [magnum_ops](https://www.reddit.com/user/magnum_ops/)

The RTMP stream is added as a "Media Source" in [Open Broadcaster Software | OBS](https://obsproject.com/) (freeware, GPL-2.0 license) and layers/filters are added to the stream in OBS.

For streaming from OBS to Facebook and LinkedIn a stream URL and stream key from [https://restream.io/](https://restream.io/) (paid account) is used.

## If you have a Mac and not a Windows/Linux pc

There is a simlair solution to this one documented by MEVO on their webpage where MEVO has created their own local RTMP server -app for MacOS which does the same as MonaServer/MonaTiny: [Multicam: Connecting to OBS](https://help.mevo.com/hc/en-us/articles/360061673871-Multicam-Connecting-to-OBS)
If you are a mac-user, you should probably use this app instead even tho MonaServer/MonaTiny has a Unix -build, but it is not as user friendly to set up.
