# Headless Server Install
There are multiple possibilities to install a headless server. Compile it from source or install it from a package manager or use docker.
- Compiling from source is detailed in the [PokerTH repository](https://github.com/pokerth/pokerth/blob/stable/docs/server_setup_howto.txt) Section 2. Installation on Linux
- Package manager
- Docker

### Server Configuration
Details can be found in the [PokerTH repository](https://github.com/pokerth/pokerth/blob/stable/docs/server_setup_howto.txt) 3. Configuration file config.xml

Somebody wrote on the pokerth.net forum that the configuration parameters are selfexplanitory. And they are. Not that complicated to figure out the meaning of them. But I think the settings are good as defaults. (might be the server password that you'd like to set).  

Config details about IRC integration can be found in the [PokerTH repository](https://github.com/pokerth/pokerth/blob/stable/docs/server_setup_howto.txt) 4. Server Admin IRC bot

Version 1.1.2 config.xml can be found [HERE](config.xml)

## Through  package manger
It is a nice and easy way to install the server. I will only explain the Debian/Ubuntu apt install method here, but the othere package manager steps are probably very similar.
Do the necessary ```apt update``` and ```apt upgrade```

Than:
```
root@maod48jh3:# apt install pokerth-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  gsfonts gsfonts-x11 libboost-atomic1.67.0 libboost-filesystem1.67.0 libboost-iostreams1.67.0 libboost-program-options1.67.0 libboost-regex1.67.0
  libboost-thread1.67.0 libfontenc1 libircclient1 libprotobuf17 libtinyxml2.6.2v5 pokerth-data x11-common xfonts-encodings xfonts-utils
The following NEW packages will be installed:
  gsfonts gsfonts-x11 libboost-atomic1.67.0 libboost-filesystem1.67.0 libboost-iostreams1.67.0 libboost-program-options1.67.0 libboost-regex1.67.0
  libboost-thread1.67.0 libfontenc1 libircclient1 libprotobuf17 libtinyxml2.6.2v5 pokerth-data pokerth-server x11-common xfonts-encodings xfonts-utils
0 upgraded, 17 newly installed, 0 to remove and 1 not upgraded.
Need to get 20.4 MB of archives.
After this operation, 51.5 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
...
root@maod48jh3:~# (installed)
```
As I noticed The server starts automatically after the install. (more details to come)

Comfiguration file (config.xml) is located ```/var/games/pokerth-server/.pokerth/config.xml```

pokerth_server can be run manually by ```/var/games/pokerth-server/pokerth_server```

## Docker
Docker is the next big thing in application deployment. [LINK](https://docs.docker.com/) PokerTH installation is as comlicated as the package manager install(not at all). The pre-requisit is to have docker installed.

Let's search the pokerth from the CLI. 
```
root@maod48jh3:# docker search pokerth
NAME                      DESCRIPTION                      STARS     OFFICIAL   AUTOMATED
rom14700/pokerth-server   A dedicated server for PokerTH   0                    
dannyk81/pokerth-server                                    0                    
shantkeh/pokerth-server                                    0                    
janmcfly/pokerth                                           0    
```
[rom14700/pokerth-server](https://hub.docker.com/r/rom14700/pokerth-server) is a good docker image I think to use.

Download it with: ```root@maod48jh3:# docker pull rom14700/pokerth-server  ```

Check the image:
```
root@maod48jh3:# docker images | grep poker
rom14700/pokerth-server        latest          8f482f671953   10 months ago   1.17GB
```
I used the following command to start the container:

```docker run --name pokerth-server -p 7234:7234  -v /path/to/config.xml:/root/.pokerth/config.xml --restart unless-stopped -d  rom14700/pokerth-server```


## Client Setup
This is where the rubber meets the road and I admit that this took me several hours to figure out what is the proper way to connect. It is very simple. If you have been trying to set it up but couldn't figure out why you are getting only a chat screen (like this) and what should you do there and how should you start the game, than here is the solution. 

Start client: 
![alt text](https://github.com/04foxsec/pokerth/blob/main/pics/pths_setting1.png "Client main screen")


