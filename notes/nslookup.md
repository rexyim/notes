

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
>but if the network admins have done their job you would not be able get this information. From a hackers perspective this is a goldmine.
>
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTg1MzE2NDU1MSwtMTA3MDMwOTc3OSwtMT
A2NDAzMTg1MV19
-->