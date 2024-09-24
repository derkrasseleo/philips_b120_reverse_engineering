# Why?
- I found this old baby camera and it couldn't connect to our wifi. Then I decided to look at how exactly that thing works
## Findings
- The camera tries to connect to some authentification server that doesn't exist anymore and get's stuck
- The camera connects to wifi by reading a QR Code that has this format:
```
["your@email.com","WIFI_SSID","WIFI_PASSWORD","Home Monitor","192.168.0.115","+01:00"]
```
- Had to disasemble the camera to get access to UART
- It's running some kind of buybox linux image
- You can change it's IP and other settings via a config file
- Here's some interesting files for configuring the camera
   - etc/lighttpd
   - etc/yoics
   - data/cfg/config.lua
   - srv/www/htdocs
-  Default username: `admin`
-  Default Password (could vary between cameras): `M100-4674448`
- There's a still image at `/cgi-bin/img-d1.cgi` (generates every 5 seconds or so) or `/cgi-bin/img-cif.cgi` (smaller)
- To reach the rtsp stream use `rtsp://admin:M100-4674448@192.168.68.54:554/stream0`

## Images
### Front of Main PCB and location of RX/TX for UART
 
 ![Front](https://github.com/derkrasseleo/philips_b120_reverse_engineering/assets/16163571/323c77d2-12fc-43e2-9365-43c96794c8a3)

### Back of Main PCB

![IMG_20230208_210111 HEIC_compressed](https://github.com/derkrasseleo/philips_b120_reverse_engineering/assets/16163571/27347b4a-9abd-4ca1-80f1-21ab3968e9ce)
