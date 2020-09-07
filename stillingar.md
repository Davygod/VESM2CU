#### Að tengjast RPi remote

1. Finndu IP á RPi
    
    - https://www.raspberrypi.org/documentation/remote-access/ip-address.md
    - `ping raspberrypi.local`
    - nmap (Network Mapper) `sudo nmap -sn 192.168.1.0/24`       
    - ýmis forrit: FRING (andrion app), Advanced IP scanner
    - subnet range í Tækniskóla er: 10.11.45.1-254

    
2. VNC
 - Notaðu VNC viewer og tengdu þið við RPi


3. SSH 
 - Tengdu þig remote við RPi með SSH `ssh pi@ipaddress` 
 - Keyrðu: `sudo raspi-config` og gerðu viðeigandi stillingar t.d. Wifi ef þú þarft


#### Wifi Tækniskólinn

```
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
country=IS
network={
    ssid="Taekniskolinn"
    key_mgmt=NONE
}
```
