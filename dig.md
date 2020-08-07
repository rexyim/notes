


># DIG
>Dig is linux/unix based command line utility which queries the DNS server for domain related records. It can be viewed as nslookup equivalent for linux environment.

>It is important to understand the output of a dig command.
>The following is a dig query of google.com.

    >axxxxx@Ubuntu-20:~$ dig google.com
    
    ; <<>> DiG 9.16.1-Ubuntu <<>> google.com
    ;; global options: +cmd
    ;; Got answer:
    ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 10815
    ;; flags: qr rd ra; QUERY: 1, ANSWER: 6, AUTHORITY: 0, ADDITIONAL: 1
    
    ;; OPT PSEUDOSECTION:
    ; EDNS: version: 0, flags:; udp: 65494
    ;; QUESTION SECTION:
    ;google.com.			IN	A
    
    ;; ANSWER SECTION:
    google.com.		261	IN	A	64.233.177.113
    google.com.		261	IN	A	64.233.177.139
    google.com.		261	IN	A	64.233.177.138
    google.com.		261	IN	A	64.233.177.102
    google.com.		261	IN	A	64.233.177.101
    google.com.		261	IN	A	64.233.177.100
    
    ;; Query time: 124 msec
    ;; SERVER: 127.0.0.53#53(127.0.0.53)
    ;; WHEN: Thu Aug 06 21:21:54 CDT 2020
    ;; MSG SIZE  rcvd: 135
>the first thing we notice is that unlike nslookup, dig doesn't provide us any details regarding the our own dns server's ip address or domain name. If we want to know our own dns server's ip address. we need to see the resolve.conf file.
>The output also shows the current version of the dig utility.

    <<>> DiG 9.16.1-Ubuntu <<>> google.com

We can shorten the length answer by using *+short* flag.

    a********@Ubuntu-20:~$ dig google.com +short
    172.253.124.139
    172.253.124.102
    172.253.124.113
    172.253.124.101
    172.253.124.100
    172.253.124.138
   >With dig i can query for any record whi
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExNzYwMjA4NCwxMjkwMjk4MTIsLTQ1MT
Q1NTE2MSwyMDQwMjk3NjIyXX0=
-->