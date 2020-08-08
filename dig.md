---


---

<blockquote>
<h1 id="dig-and-host">DIG and HOST</h1>
<p>Dig is linux/unix based command line utility which queries the DNS server for domain related records. It can be viewed as nslookup equivalent for linux environment.</p>
</blockquote>
<blockquote>
<p>It is important to understand the output of a dig command.<br>
The following is a dig query of <a href="http://google.com">google.com</a>.</p>
</blockquote>
<pre><code>&gt;axxxxx@Ubuntu-20:~$ dig google.com

; &lt;&lt;&gt;&gt; DiG 9.16.1-Ubuntu &lt;&lt;&gt;&gt; google.com
;; global options: +cmd
;; Got answer:
;; -&gt;&gt;HEADER&lt;&lt;- opcode: QUERY, status: NOERROR, id: 10815
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
</code></pre>
<blockquote>
<p>the first thing we notice is that unlike nslookup, dig doesn’t provide us any details regarding the our own dns server’s ip address or domain name. If we want to know our own dns server’s ip address. we need to see the resolve.conf file in /etc.</p>
</blockquote>
<blockquote>
<p>The output also shows the current version of the dig utility.</p>
</blockquote>
<pre><code>&lt;&lt;&gt;&gt; DiG 9.16.1-Ubuntu &lt;&lt;&gt;&gt; google.com
</code></pre>
<blockquote>
<p>We can shorten the length of the out put  by using <em>+short</em> flag.</p>
</blockquote>
<pre><code>a********@Ubuntu-20:~$ dig google.com +short
172.253.124.139
172.253.124.102
172.253.124.113
172.253.124.101
172.253.124.100
172.253.124.138
</code></pre>
<blockquote>
<p>With dig i can query for any record by just specifying it the following way</p>
</blockquote>
<pre><code>*get the address(es) for yahoo.com*
dig yahoo.com A 

 *get a list of yahoo's mail servers*
dig yahoo.com MX 

 *get a list of DNS servers authoritative for yahoo.com*
dig yahoo.com NS 

 *get all of the above*
dig yahoo.com ANY 
</code></pre>
<blockquote>
<h3 id="reverse-lookup">Reverse Lookup</h3>
<p>Use the <code>-x</code> option to lookup the main hostname associated with an IP address thats it.</p>
</blockquote>
<pre><code>&gt;a*******@Ubuntu-20:~$ dig -x 64.233.177.113 +short
yx-in-f113.1e100.net.
</code></pre>
<blockquote>
<p>There are a whole lot of other options we can try. The dig man page has all the ways the utility can be utilized.</p>
</blockquote>
<blockquote>
<h1 id="host">Host</h1>
<p>host is also a simple utility for performing DNS lookups. It is normally used to convert names to IP addresses and vice versa.<br>
The usage is</p>
</blockquote>
<pre><code>a*******@Ubuntu-20:~$ host 
host: illegal option -- h
Usage: host [-aCdilrTvVw] [-c class] [-N ndots] [-t type] [-W time]
            [-R number] [-m flag] hostname [server]
            
a*******@Ubuntu-20:~$ host -t A  google.com 
google.com has address 64.233.177.113
google.com has address 64.233.177.102
google.com has address 64.233.177.139
google.com has address 64.233.177.101
google.com has address 64.233.177.138
google.com has address 64.233.177.100
</code></pre>

