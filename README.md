# rtl8821cu
Linux Driver for Realtek 8821cu

# patch for ap mode
Add patch for Original Driver to support 802.11AC AP mode in Linux 4.0 above
The driver has been tested on Ubuntu 17.10 with kernel 4.13.36 and arch X86_64 successfully
Both AP and STA and Monitor mode can work.
Monitor mode Start:
```sh
# iw dev wlan0 interface add mon0 type monitor
# ifconfig wlan0 down
# ifconfig mon0 up
# iw dev mon0 set type monitor
```

HT40 example, it seems the RTL8821CU doesn't support 11AC monitor
```sh
# iw dev mon0 set channel 36 HT40+
```

OR HT20
```sh
# iw dev mon0 set channel 1 HT20
```

Capture Tool is: cmd: tcpdump or gui: wireshark
```sh
# tcpdump -i mon0 -y ieee802_11_radio 
```

OR GUI tool wireshare     /*Note Start with root previlidge and select mon0 to capture*/

But the monitor can't receive all air packets which is corresponding to the right setting channel

802.11AC mode can work perfectly with Official Standard hostapd Release with 2.4 version above
1X1 AC TP of iperf TX will be 220-230Mbps, test with PC as iperf client, iphone se as iperf server.
