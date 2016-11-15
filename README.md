## trafficcop

###Basic Idea/Motivation
* The idea is to allow people to connect to a wifi hotspot and then immediately be able to simulate shitty mobile network connections.
* Lets developers easily test application performance with on slow connection in mind
* Relates to “mobile first” thinking by acknowledging “mobile first” means connections that are not always as reliable/speedy/generally good (i.e. 💩).

![Demo](demo.gif)

### Official Supported Device:

* TL-WR703N: http://www.dx.com/p/tp-link-tl-wr703n-mini-3g-2-4ghz-802-11b-g-n-150mbps-wireless-router-blue-158552
* Netgear WNDR3700v2

###Specification

* Ability to introduce extra:
 * Latency (delay)
 * Packet loss
 * Bandwidth limitations
 * Per device address throttling → i.e. web interface such that you can go and adjust the setting for your client only.

Accessible at `http://<router ip>:8080`

### Installation ###

To install this, compile an ipk and install it on your device:

    # opkg update
    # opkg install trafficcop-*.ipk

This should install and start trafficcop on 8080 with uhttpd on the ip address for the interface `br-lan`. If you're unsure what IP this is, you can run the following to find out:

    # ifconfig br-lan | grep 'inet addr' | cut -d ":" -f 2 | cut -d " " -f 1

This means you can access traffic cop at `http://<router ip>:8080`. 

### Changelog ###

- Updated from original source to work with default network on openwrt ( 192.168.1.x ).
- Fixed a bug in current_profile which was returning the status of a fixed IP instead of the current client.
- Original source was only applying rules to the down link, now rules are applied both for download/upload.
- Updated some profiles.

### TODO ###

- Cleanup cleanly the tc class after a reset
- ...
