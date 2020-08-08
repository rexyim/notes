


> # HPING3

> hping3 at its basic is a network tool which can be used to send custom TCP/IP packets and to display target replies like ping program does with ICMP replies.  So its an icmp but with a lot of bells and whistls. 
> hping3 handle fragmentation, arbitrary packets body and size and can be used in order to transfer files encapsulated under supported protocols. Using hping3 you are able to perform at least the following stuff:

> - Test firewall rules  
> - Advanced port scanning  
> - Test net performance using different protocols,  
packet size, TOS (type of service) and fragmentation.  
> - Path MTU discovery  
> - Transferring files between even really fascist firewall  
rules.  
> - Traceroute-like under different protocols.  
> - Firewalk-like usage.  
> - Remote OS fingerprinting.  
> - TCP/IP stack auditing.  
> - A lot of others.

hping3 provides lots of options all can be viewed by -h.

    root@kali:~# hping3 -h  
    usage: hping3 host [options]  
    -h --help show this help  
    -v --version show version  
    -c --count packet count  
    -i --interval wait (uX for X microseconds, for example -i u1000)  
    --fast alias for -i u10000 (10 packets for second)  
    --faster alias for -i u1000 (100 packets for second)  
    --flood sent packets as fast as possible. Don't show replies.  
    -n --numeric numeric output  
    -q --quiet quiet  
    -I --interface interface name (otherwise default routing interface)  
    -V --verbose verbose mode  
    -D --debug debugging info  
    -z --bind bind ctrl+z to ttl (default to dst port)  
    -Z --unbind unbind ctrl+z  
    --beep beep for every matching packet received  
    Mode  
    default mode TCP  
    -0 --rawip RAW IP mode  
    -1 --icmp ICMP mode  
    -2 --udp UDP mode  
    -8 --scan SCAN mode.  
    Example: hping --scan 1-30,70-90 -S www.target.host  
    -9 --listen listen mode  
    IP  
    -a --spoof spoof source address  
    --rand-dest random destionation address mode. see the man.  
    --rand-source random source address mode. see the man.  
    -t --ttl ttl (default 64)  
    -N --id id (default random)  
    -W --winid use win* id byte ordering  
    -r --rel relativize id field (to estimate host traffic)  
    -f --frag split packets in more frag. (may pass weak acl)  
    -x --morefrag set more fragments flag  
    -y --dontfrag set don't fragment flag  
    -g --fragoff set the fragment offset  
    -m --mtu set virtual mtu, implies --frag if packet size > mtu  
    -o --tos type of service (default 0x00), try --tos help  
    -G --rroute includes RECORD_ROUTE option and display the route buffer  
    --lsrr loose source routing and record route  
    --ssrr strict source routing and record route  
    -H --ipproto set the IP protocol field, only in RAW IP mode  
    ICMP  
    -C --icmptype icmp type (default echo request)  
    -K --icmpcode icmp code (default 0)  
    --force-icmp send all icmp types (default send only supported types)  
    --icmp-gw set gateway address for ICMP redirect (default 0.0.0.0)  
    --icmp-ts Alias for --icmp --icmptype 13 (ICMP timestamp)  
    --icmp-addr Alias for --icmp --icmptype 17 (ICMP address subnet mask)  
    --icmp-help display help for others icmp options  
    UDP/TCP  
    -s --baseport base source port (default random)  
    -p --destport [+][+]<port> destination port(default 0) ctrl+z inc/dec  
    -k --keep keep still source port  
    -w --win winsize (default 64)  
    -O --tcpoff set fake tcp data offset (instead of tcphdrlen / 4)  
    -Q --seqnum shows only tcp sequence number  
    -b --badcksum (try to) send packets with a bad IP checksum  
    many systems will fix the IP checksum sending the packet  
    so you'll get bad UDP/TCP checksum instead.  
    -M --setseq set TCP sequence number  
    -L --setack set TCP ack  
    -F --fin set FIN flag  
    -S --syn set SYN flag  
    -R --rst set RST flag  
    -P --push set PUSH flag  
    -A --ack set ACK flag  
    -U --urg set URG flag  
    -X --xmas set X unused flag (0x40)  
    -Y --ymas set Y unused flag (0x80)  
    --tcpexitcode use last tcp->th_flags as exit code  
    --tcp-mss enable the TCP MSS option with the given value  
    --tcp-timestamp enable the TCP timestamp option to guess the HZ/uptime  
    Common  
    -d --data data size (default is 0)  
    -E --file data from file  
    -e --sign add 'signature'  
    -j --dump dump packets in hex  
    -J --print dump printable characters  
    -B --safe enable 'safe' protocol  
    -u --end tell you when --file reached EOF and prevent rewind  
    -T --traceroute traceroute mode (implies --bind and --ttl 1)  
    --tr-stop Exit when receive the first not ICMP in traceroute mode  
    --tr-keep-ttl Keep the source TTL fixed, useful to monitor just one hop  
    --tr-no-rtt Don't calculate/show RTT information in traceroute mode  
    ARS packet description (new, unstable)  
    --apd-send Send the packet described with APD (see docs/APD.txt)

> So why hping3 is so useful ?
> so imagine a scenario where the device you are trying to enumerate is not responsive to icmp.  With hping3 we can send spl packets to specific or all ports to enumerate the device.

>Here are some basic usage of hping3
>Lets start with basic ping scan

    >~$ sudo hping3 -1 google.com
    >HPING google.com (ens33 172.253.124.139): icmp mode set, 28 headers + 0 data bytes
    len=46 ip=172.253.124.139 ttl=108 id=0 icmp_seq=0 rtt=36.0 ms
    len=46 ip=172.253.124.139 ttl=108 id=0 icmp_seq=1 rtt=27.0 ms
    len=46 ip=172.253.124.139 ttl=108 id=0 icmp_seq=2 rtt=26.0 ms
    len=46 ip=172.253.124.139 ttl=108 id=0 icmp_seq=3 rtt=25.0 ms

>Lets try a UDP scan now.

    ~$ sudo hping3 -2 192.168.10.1 -p 53
>-p flag specifies the port number. We can even specify a range like

    ~$ sudo hping3 -2 192.168.10.1 -p 21-90

>or different ports

    ~$ sudo hping3 -2 192.168.10.1 -p 53,123
 
 > hping3 can also perform the basic scans

      -M  --setseq     set TCP sequence number
      -L  --setack     set TCP ack
      -F  --fin        set FIN flag
      -S  --syn        set SYN flag
      -R  --rst        set RST flag
      -P  --push       set PUSH flag
      -A  --ack        set ACK flag
      -U  --urg        set URG flag
      -X  --xmas       set X unused flag (0x40)
      -Y  --ymas       set Y unused flag (0x80
> and address spoofing can be achieve by ***-a*** flag
> sudo hping3 -s 
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwMzE2MDAxOTcsMjM3NjQxNzMsMTI0MD
YxMTEzNiw2ODAwOTE3NDgsLTIyNzgyOTIzNywtMTc3MDQ1ODcw
NiwtMzIzNTY5OTY4LC0xNzk1ODIyMTEwXX0=
-->