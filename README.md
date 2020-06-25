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

If you get 'Unable to locate Java. Please set JAVA_HOME environment variable' error message when you run red5 server, you can fix the error by modifying red5.sh. 
```c
vi red5.sh
```
Add /usr/local/java/bin/java 
```c
for JAVA in "/usr/bin/java" "/usr/local/bin/java" "${JAVA_HOME}/bin/java" "${JAVA_HOME}/Home/bin/java" "/usr/local/java/bin/java"
```
