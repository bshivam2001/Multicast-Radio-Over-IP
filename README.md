# Multicast-Radio-Over-IP
Host and stream your favourite multimedia over the internet

## How to Run
### Prerequisites
- Install gtk library
<br>  ```sudo apt install libgtk-3-dev```
- Install FFmpeg tool
<br>  ```sudo apt install ffmpeg```
- 8 multimedia files for the stations to playback:
  - f<1-4>.mp3 for station 1
  - vid<5-8>.mp4 for station 2
 - Convert the videos to mpegts format in an mp4 container for it to be streamable. Use the following command to convert:
   <br>  ```ffmpeg -i inputfile.mp4 -f mpegts output_file.mp4```

### Compilation
**On the host side**
- Compile server.c
  <br> ```gcc -o server server.c```
- Compile station1.c
  <br> ```gcc -o station1 station1.c```
- Compile station2.c
  <br> ```gcc -o station2 station2.c```
  
**On the client side**
- Compile client.c with the gtk flag
  <br> ```gcc `pkg-config --cflags gtk+-3.0` -o client client.c `pkg-config --libs gtk+-3.0` ```
- Compile receiver.c
  <br> ```gcc -o receiver receiver.c```

### Execution
**On the host side**
1. Ensure the media files are in the same directory, then run the server
  <br> ```./server```
2. Run station1 with the IP 239.192.4.1 as the launch argument
  <br> ```./station1 239.192.4.1```
3. Run station2 with the IP 239.192.4.2 as the launch argument
  <br> ```./station2 239.192.4.2
  
**On the client side**
1. Run the client as an admin with the server's IP address as the launch argument
  <br> ```sudo ./client <Server IP>```
  <br> If you're running on local host, use the IP *127.0.0.1*
2. Press Station 1 or Station 2 button to start streaming


 
