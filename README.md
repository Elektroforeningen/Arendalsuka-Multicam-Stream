# Arendalsuka-Multicam-Stream
This repository is both a "how to" and documentation for how The Electrical Association in Norway set up their live streams during Arendalsuka 2024 for both Facebook and LinkedIn with multiple Logitech MEVO cameras and RØDE microphones.

# Table of contents:
* [Hardware](https://github.com/Elektroforeningen/Arendalsuka-Multicam-Stream/edit/main/README.md#hardware)
* [Hardware diagram](https://github.com/Elektroforeningen/Arendalsuka-Multicam-Stream/edit/main/README.md#hardware-diagram)
* [Software](https://github.com/Elektroforeningen/Arendalsuka-Multicam-Stream/edit/main/README.md#software)

# Hardware

* [MEVO start camera 3-Pack](https://www.mevo.com/no-NO/products/mevo-start-3-pack)
* Windows 11 Laptop
* iPad
* 5G wifi router
* [RØDE Wireless GO II](https://rode.com/en/microphones/wireless/wirelessgoii?variant_sku=WIGOII) (2 microphones 1 receiver)
* [Bose S1 Pro speaker](https://support.bose.com/s/product/s1-pro-portable-bluetooth-speaker-system/01t8c00000OydMeAAJ?language=en_US) (for the audience at location)
* 3.5mm minijack splitter
* 3.5mm cables
* [Apple USB C Digital AV multiport adapter](https://www.apple.com/shop/product/MW5M3AM/A/usb-c-digital-av-multiport-adapter)

# Hardware diagram

Digram of the hardware-setup used, made using [https://draw.io/](https://draw.io/)

![Arendalsuka-Multicam-Stream.png](Arendalsuka-Multicam-Stream.png)

# Software

The MEVO cameras are connected to the iPad using the [Logitech Mevo Multicam App](https://apps.apple.com/us/app/logitech-mevo-multicam/id1503021034).

The RØDE Receiver is set up using the [RØDE Central Mobile App](https://apps.apple.com/us/app/r%C3%B8de-central-mobile/id1576314986) 

The Laptop is receiving the RTMP stream from the Mevo Multicam app on the iPad using [MonaServer (MonaTiny version)](https://sourceforge.net/projects/monaserver/)

The setup for MonaServer/MonaTiny is from the thread [How do I turn my PC into a local RTMP server? So Mevo can broadcast to it locally](https://www.reddit.com/r/mevocamera/comments/bd5182/how_do_i_turn_my_pc_into_a_local_rtmp_server_so/) on the subreddit [r/mevocamera](https://www.reddit.com/r/mevocamera/) by Reddit-user [magnum_ops](https://www.reddit.com/user/magnum_ops/)

The RTMP stream is added as a "Media Source" in [Open Broadcaster Software | OBS](https://obsproject.com/) and layers/filters is added to the stream in OBS.

For streaming from OBS to Facebook and LinkedIn a stream url and stream key from [https://restream.io/](https://restream.io/) is used.
