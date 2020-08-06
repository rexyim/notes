

># NSLOOKUP

>At its core nslookup is a tool used to gain information from DNS server.
>Before you even play with nslookup you need to understand DNS and how exactly it works. The following link will give you a brief understanding of DNS.
>Nslookup is a window based utility and can be launched in two modes.

> - Interactive 
> - non-interactive

> The interactive more is way more fun than the non-interactive one. Obviously, if you have a simple query you can get it done with non-interactive mode for e.g

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
>Microsoft docs provide all the functionalities we can achieve with nslookup.
>[Microsoft Nslookup Docs](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/nslookup)
 
 >Lets try some fun ones out
 
 >### ls 
 >Well ls pretty much does the exact thing it does on linux system but with a twist.
 >Once you go interactive by typing
 

    C:\Users\a..........r>nslookup 
        Server:  $.$.$.$
        Address:  #.#.#.#
     >
>you can type the following

    ls [<option>] <DNSdomain> [{[>] <filename>|[>>] <filename>}]
>and try bunch of options like.

    -   **-t:**  Lists all records of the specified type. For more information, see  [nslookup set querytype](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/nslookup-set-querytype).
    -   **-a:**  Lists aliases of computers in the DNS domain. This parameter is the same as  **-t CNAME**
    -   **-d:**  Lists all records for the DNS domain. This parameter is the same as  **-t ANY**
    -   **-h:**  Lists CPU and operating system information for the DNS domain. This parameter is the same as  **-t HINFO**
    -   **-s:**  Lists well-known services of computers in the DNS domain. This parameter is the same as  **-t WKS**
>but if the network admins have done their job you would not be able get this information. From a hackers perspective this info is a goldmine.

>### Set
>Set is another big one.
>for e.g If you are looking for a specific record type in DNS, you can set it with the following

    >set type=MX 
>This will set the type of record we are looking for which in the above case is mail exchanger.
>after this you can query the DNS server with ip or domain and it will return only the specific related record. For e.g

    > set type=A
    > google.com
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

>### query
>This displays information regarding processes, sessions, and Remote Desktop Session Host servers. For e.g
>
>
<!--stackedit_data:
eyJoaXN0b3J5IjpbNTM1MDY3OTY5LDcxNTU0NDU3MCwxMzE4ND
UyNzMxLC0xMDcwMzA5Nzc5LC0xMDY0MDMxODUxXX0=
-->