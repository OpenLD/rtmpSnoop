# rtmpsnoop - The RTMP sniffer!

## Difference between Original rtmpSnoop

* Supports more than one output format at the same time.
* Default output is rtmpdump.
* Small changes in rtmpdump format.
* lib/ was changed to rtmpsnoop_lib/ so you can put that in your python library folder.
* Support multiple videos.

## Contributors

https://github.com/OpenLD/rtmpsnoop/graphs/contributors

## Original repository by Andrea Fabrizi

https://github.com/andreafabrizi/rtmpSnoop

Original for can be found on https://github.com/andreafabrizi/rtmpSnoop and I will try to stay in sync with original upstream as long as it will be possible for me to maintain. At this point there is all features and bugfixes as is in original upstream.

This repo is initially thought to be used in enigma2, it may not work correctly on other architectures.
Actual code may vary in upcoming commits.

**rtmpsnoop** lets you to sniff RTMP streams from live TV, online channels and straming services and dump the RTMP properties in many formats.
You can analyse both live and dumped streams.

## Features

* Live sniffing from one ore more interfaces
* Read dumped streams from PCAP files
* Dump the RTMP properties in more formats (simple list, m3u entry or rtmpdump syntax)
* Easy to use and cross platform!

## Requirements

To run it you need only python (at least 2.7 version) and the scapy module. 

**Linux Installation**  
* Debian/Ubuntu:  
`apt-get install python-scapy`

* RedHat/Centos:  
`yum install scapy.noarch`  
`yum install python-argparse.noarch`  

**Mac Installation**  

* Download pcapy from http://corelabs.coresecurity.com/
* Download dnet from http://libdnet.sourceforge.net/

Unzip and cd in to dnet file then

```
 CFLAGS='-arch i386 -arch x86_64' ./configure --prefix=/usr
 archargs='-arch i386 -arch x86_64' make
 sudo make install
 cd python
 sudo python setup.py install
```

**Windows Installation**  
Follow this guide to install scapy module on windows:
http://www.secdev.org/projects/scapy/doc/installation.html#windows

## Get the code
```
git clone https://github.com/OpenLD/rtmpsnoop.git
```

## Usage

The syntax is quite simple:

```
$python rtmpsnoop -h
usage: rtmpsnoop [-h] [-i DEVICE | -f PCAPFILE]
                    [--out-list ][ --out-m3u ][ --out-rtmpdump] [-p PORT]
                    [--one] [--quiet] [--debug]

rtmpSnoop lets you to grab the RTMP properties from live or dumped streams.

optional arguments:
  -h, --help      show this help message and exit

Input:
  -i DEVICE       Device to sniff on (Default: sniffs on all devices)
  -f PCAPFILE     PCAP file to read from

Output format:
  --out-list      Prints the RTMP data as list
  --out-m3u       Prints the RTMP data as m3u entry
  --out-rtmpdump  Prints the RTMP data in the rtmpdump format (Default)

Additional options:
  -p PORT         RTMP port (Default: sniffs on all ports)
  --one           Quit after the first stream found
  --quiet         Doesn't print anything except the RTMP output
  --debug         Enable DEBUG mode
```

## Examples

Sniffing on all interfaces, without filters:
```
sudo python rtmpsnoop
```

Sniffing on eth0, and looking for RTMP streams on port 1935 only:
```
sudo python rtmpsnoop -i eth0 -p 1935
```

Reading streams from PCAP file:
```
python rtmpsnoop -f dump/tv.pcap
```
