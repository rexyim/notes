


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
>the first thing we notice is that unlike nslookup 
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTI5MDI5ODEyLC00NTE0NTUxNjEsMjA0MD
I5NzYyMl19
-->