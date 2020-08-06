




># NSLOOKUP

>At its core nslookup is a tool used to gain information from DNS server.
>Before you even play with nslookup you need to understand DNS and how exactly it works. The following link will give you a brief understanding of DNS.
>[CLOUDFLARE DNS](https://www.cloudflare.com/learning/dns/what-is-dns)

>Nslookup is a window based utility and can be launched in two modes.
> - Interactive 
> - non-interactive

> The interactive  is way more fun than the non-interactive one. Obviously, if you have a simple query you can get it done with non-interactive mode for e.g

    C:\Users\a..........r>nslookup google.com
        Server:  $.$.$.$
        Address:  #.#.#.#
        
    Non-authoritative answer:
        Name:    google.com
        Addresses:  2607:f8b0:4002:c02::71
                  2607:f8b0:4002:c02::8b
                  2607:f8b0:4002:c02::66
                  108.177.122.138
                  108.177.122.102
                  108.177.122.139
                  108.177.122.101
                  108.177.122.113
                  108.177.122.100

> But why be non-interactive when interaction is so much fun.
> To be interactive Type a hyphen (-) then your chosen parameter and then the name or IP address.
>Microsoft docs provide all the functionalities we can achieve with nslookup.
>[Microsoft Nslookup Docs](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/nslookup)

 >Lets try some fun ones out

>### help
>This is the most important one out of all of them. If you get stuck i nslookup type help or ? and press enter. VOLA

    C:\Users\ap.........>nslookup -all ?
    Default Server:  (null)
    
    Set options:
      nodebug
      defname
      search
      recurse
      nod2
      novc
      noignoretc
      port=53
      type=A+AAAA
      class=IN
      timeout=2
      retry=1
      root=A.ROOT-SERVERS.NET.
      domain=xx.xxx.xxx
      MSxfr
      IXFRversion=1
      srchlist=xxxx/xxxxx/xxxxxxx

>### -Type
>If you are looking for a specific record type in DNS, you can set it with the following

    C:\Users\ap.........>nslookup -type=A  google.com
>This will set the type of record we are looking for which in the above case is mail exchanger.
>after this you can query the DNS server with ip or domain and it will return only the specific related record. For e.g
 
    google.com
        Server:  $.$.$.$
        Address:  #.#.#.#
    
        Non-authoritative answer:
        Name:    google.com
        Addresses:  108.177.122.113
                  108.177.122.100
                  108.177.122.101
                  108.177.122.138
                  108.177.122.139
                  108.177.122.102
>preety cool right !
>Below are all the records type you can look for with nslookup.

    >-   **A:**  Specifies a computer's IP address.
    -   **ANY:**  Specifies a computer's IP address.
    -   **CNAME:**  Specifies a canonical name for an alias.
    -   **GID**  Specifies a group identifier of a group name.
    -   **HINFO:**  Specifies a computer's CPU and type of operating system.
    -   **MB:**  Specifies a mailbox domain name.
    -   **MG:**  Specifies a mail group member.
    -   **MINFO:**  Specifies mailbox or mail list information.
    -   **MR:**  Specifies the mail rename domain name.
    -   **MX:**  Specifies the mail exchanger.
    -   **NS:**  Specifies a DNS name server for the named zone.
    -   **PTR:**  Specifies a computer name if the query is an IP address; otherwise, specifies the pointer to other information.
    -   **SOA:**  Specifies the start-of-authority for a DNS zone.
    -   **TXT:**  Specifies the text information.
    -   **UID:**  Specifies the user identifier.
    -   **UINFO:**  Specifies the user information.
    -   **WKS:**  Describes a well-known service.

>### -query
>This displays information regarding processes, sessions, and Remote Desktop Session Host servers. For e.g

    >C:\Users\ap.........>nslookup -query=mx cloudns.net
        Server:  $.$.$.$
        Address:  #.#.#.#
    
    Non-authoritative answer:
    cloudns.net     MX preference = 10, mail exchanger = ALT3.ASPMX.L.GOOGLE.COM
    cloudns.net     MX preference = 1, mail exchanger = ASPMX.L.GOOGLE.COM
    cloudns.net     MX preference = 5, mail exchanger = ALT1.ASPMX.L.GOOGLE.COM
    cloudns.net     MX preference = 10, mail exchanger = ALT4.ASPMX.L.GOOGLE.COM
    cloudns.net     MX preference = 5, mail exchanger = ALT2.ASPMX.L.GOOGLE.COM
>Here we are checking the MX records of the mail servers.

>### -Debug
>Debug is another one which is quite helpful. By turning debug mode on you can view more information about the packet sent to the server and the resulting answer.

>### server
>This command uses the current default server to look up the information about the specified DSN domain.

    >C:\Users\ap.........>nslookup server <DNSdomain>

>### ls
>Lists DNS domain information.


>### -query
>Try some out and you will find nslookup to be a really handy tool in your arsenal.

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEwNjU4MjgxNTNdfQ==
-->