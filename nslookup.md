---


---

<hr>
<hr>
<hr>
<hr>
<blockquote>
<h1 id="nslookup">NSLOOKUP</h1>
</blockquote>
<blockquote>
<p>At its core nslookup is a tool used to gain information from DNS server.<br>
Before you even play with nslookup you need to understand DNS and how exactly it works. The following link will give you a brief understanding of DNS.
<a href="https://www.cloudflare.com/learning/dns/what-is-dns/">DNS  Cloudflare</a>
<br>
Nslookup is a window based utility and can be launched in two modes.</p>
</blockquote>
<blockquote>
<ul>
<li>Interactive</li>
<li>non-interactive</li>
</ul>
</blockquote>
<blockquote>
<p>The interactive is way more fun than the non-interactive one. Obviously, if you have a simple query you can get it done with non-interactive mode for e.g</p>
</blockquote>
<pre><code>C:\Users\a..........r&gt;nslookup google.com
    Server:  $.$.$.$
    Address:  #.#.#.#
</code>
Name:    <a href="http://google.com">google.com</a><br>
<pre><code>Addresses:  2607:f8b0:4002:c02::71&lt;br&gt;
</code></pre>
</pre><p>2607:f8b0:4002:c02::8b<br><br>
2607:f8b0:4002:c02::66<br><br>
108.177.122.138<br><br>
108.177.122.102<br><br>
108.177.122.139<br><br>
108.177.122.101<br><br>
108.177.122.113<br></p>
<pre><code>          108.177.122.138
      108.177.122.102
      108.177.122.139
      108.177.122.101
      108.177.122.113
      108.177.122.100&lt;br&gt;
</code></pre>
<p>108.177.122.100</p>
<blockquote>
<p>But why be non-interactive when interaction is so much fun.<br>
To be interactive Type a hyphen (-) then your chosen parameter and then the name or IP address.<br>
Microsoft docs provide all the functionalities we can achieve with nslookup.<br>
<a href="https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/nslookup">Microsoft Nslookup Docs</a></p>
</blockquote>
<blockquote>
<p>Lets try some fun ones out</p>
</blockquote>
<blockquote>
<h3 id="help">help</h3>
<p>This is the most important one out of all of them. If you get stuck i nslookup type help or ? and press enter. VOLA</p>
</blockquote>
<pre><code>C:\Users\ap.........&gt;nslookup -all ?
Default Server:  (null)
</code></pre><p>
Set options:<br>
nodebugdefname<br>
search<br>
</p><p>recurse<br><br>
nod2<br><br>
novc<br></p>
<p>nod2<br>
noignoretc<br><br>
port=53type=A+AAAA<br><br>
class=IN timeout=2<br></p>
<p>retry=1<br><br>
<a href="http://
  root=A.ROOT-SERVERS.NET">root=A.ROOT-SERVERS.NET</a>.<br><br>
<a href="http://domain=xx.xxx.xxx">domain=xx.xxx.xxx</a><br><br>
MSxfr<br><br>
IXFRversion=1<br><br>
srchlist=xxxx/xxxxx/xxxxxxx<br></p>

<blockquote>
<h3 id="type">-Type</h3>
<p>If you are looking for a specific record type in DNS, you can set it with the following</p>
</blockquote>
<pre><code>C:\Users\ap.........&gt;nslookup -type=A  google.com
</code></pre>
<blockquote>
<p>This will set the type of record we are looking for which in the above case is mail exchanger.<br>
after this you can query the DNS server with ip or domain and it will return only the specific related record. For e.g</p>
</blockquote>
<pre><code>google.com
    Server:  $.$.$.$
    Address:  #.#.#.#
</code><pre><code>Non-authoritative answer:
Name:    google.comAddresses:  108.177.122</code></pre>
</pre><p></p>
<blockquote>
<p>preety cool right !<br>
Below are all the records type you can look for with nslookup.</p>
</blockquote>
<pre><code>&gt;-   **A:**  Specifies a computer's IP address.
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
</code></pre>
<blockquote>
<h3 id="query">-query</h3>
<p>This displays information regarding processes, sessions, and Remote Desktop Session Host servers. For e.g</p>
</blockquote>
<pre><code>&gt;C:\Users\ap.........&gt;nslookup -query=mx cloudns.net
    Server:  $.$.$.$
    Address:  #.#.#.#
</code></pre><p>
Non-authoritative answer:<br>
</p>
