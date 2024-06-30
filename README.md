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
- You can change it's IP and other settings via a config file (
- To reach the rtsp stream use `admin:M100-4674448@rtsp://admin:M100-4674448@192.168.68.82:554/stream0`
 ![image](https://github.com/derkrasseleo/philips_b120_reverse_engineering/assets/16163571/323c77d2-12fc-43e2-9365-43c96794c8a3)
