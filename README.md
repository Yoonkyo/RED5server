# RED5 server
Red5 streaming server for video and live streaming

# 1. Windows 
Installation guide on windows 10 and test on local environment 

## Install RED5 Server
To install the Red5 Server:
1. Download red5-server-1.2.3.zip (Link: https://github.com/Red5/red5-server)

2. Unzip and move this file to C:\ (E.g. C:\red5-server)

3. Set environment variable path
- Name: RED5_HOME 
- Value: C:\red5-server

## Run Red5 
Execute red5.bat (This file is located in C:\red5-server)

## Verify Red5 is Running
You can verify that it is running and available by visiting your instance at port 5080.

Open a web browser and navigate to http://localhost:5080/

If you can enter the default page of RED5, your server is running.

## Red5 Streaming Demo
### Video Streming
1. Click 'demo' on the default page of RED5

2. Click 'OFLA Demo - Classic demo'

3. Move your video file to C:\red5-server\webapps\oflaDemo\streams

4. Click Connect button (You can find your video file on the video list)

5. If you click video that you want to play, the video start to play
 
### Live Streaming
1. Click 'demo' on the default page of RED5

2. Click 'Publisher'

3. Click 'Connect' and set Video and Audio

4. Change the streaming name and click publish


# 2. Linux
Installation guide on Linux (Ubuntu 18.04) and test RTMP connection

## Install RED5 Server
To install the Red5 Server:
1. Download red5-server-1.2.3.zip (Link: https://github.com/Red5/red5-server)

2. Move my current directory to /usr/local
```c
cd /usr/local
```

3. Move red5-server-1.2.3.zip to /usr/local and unzip the file
```c
sudo unzip red5-server-1.2.3.zip
```

4. Add execute permission to following files:
- red5.sh
- red5-shutdown.sh
- red5-debug.sh 
```c
sudo chmod +x *.sh
```

5. Run Red5 server
```c
sudo./red5.sh
```

If you get 'Unable to locate Java. Please set JAVA_HOME environment variable' error message, you can fix the error by modifying red5.sh. 
```c
vi red5.sh
```
Add /usr/local/java/bin/java 
```c
for JAVA in "/usr/bin/java" "/usr/local/bin/java" "${JAVA_HOME}/bin/java" "${JAVA_HOME}/Home/bin/java" "/usr/local/java/bin/java"
```

## Open Port for RED5 Server
Open 1935, 1936, 3690, 5080, 8088 port
```c
sudo iptables -I INPUT 1 -p tcp --dport 1935 -j ACCEPT
sudo iptables -I INPUT 1 -p tcp --dport 1936 -j ACCEPT
sudo iptables -I INPUT 1 -p tcp --dport 3690 -j ACCEPT
sudo iptables -I INPUT 1 -p tcp --dport 5080 -j ACCEPT
sudo iptables -I INPUT 1 -p tcp --dport 8088 -j ACCEPT
```

## Check RTMP connection
### Video Streaming
1) Move a video file to "Your_Red5_route/oflaDemo/streams" directory 

2) Test with your video player (connect rtmp://localhost:1935/oflaDemo/videofile)

If you want to change oflaDemo to other name, edit web.xml and red5-web.properties located in ~/oflaDemo/WEB-INF

### Live Streaming
Use broadcast application to publish your live streaming. I utilized OBS studio.

1) Connect rtmp://localhost:1935/live and set your broadcast name(e.g. myobsstream)

2) Set other configure (Audio, Mic..) 

3) Click 'start streaming'

4) Test with your video player (connect rtmp://localhost:1935/live/myobsstream)

If you want to change live to other name, edit web.xml and red5-web.properties located in ~/live/WEB-INF
