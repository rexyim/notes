---


---

<blockquote>
<h1 id="cross-site-request-forgery-csrf">Cross-Site Request Forgery (CSRF)</h1>
</blockquote>
<blockquote>
<p>Some times when i am reading a technical article or trying to understand a technical concept, i always wish if someone could explain to me like i am a 5 year old.<br>
So in the same spirit i am going to try explain CSRF like am explaining to a 5 year old.</p>
</blockquote>
<blockquote>
<p>Imagine that i am a regular customer to a candy store and the entry to the candy store can only be granted if you know the secret phrase that you need to tell the guard of the candy store.<br>
Now lets say a bad kid x not only tricks you to reveal the secret phrase but also does a good job of impersonating you. The candy store guard has no way to know if its you or the bad kid x asking to get in the candy store.</p>
</blockquote>
<blockquote>
<p>This is exactly what happens  with CSRF.  The candy  store can be your bank, the malicious attacker is the bad kid x and the secret phrase is your sessioni for that bank website.</p>
</blockquote>
<blockquote>
<p>Imagine one day you, an unsuspecting bank user, also happened to be logged in to the bank website <a href="http://bank.com">bank.com</a>. This will create an active session cookies at your end.<br>

> The malicious attacker will send a an HTML e-mail including something like the following tag</p>
</blockquote>
<pre><code>&lt;img src="https://www.bank.com/transfer?amount=1000&amp;amp;destination=malicious -attacker"&gt;
</code></pre>
<blockquote>
<p>not just to you but to 100s other bank customers.<br>
If you have a web mail client that loads images automatically, which is practically every web mail client nowadays, the transfer request will be made from your browser using your IP address and <em>_your <a href="http://bank.com">bank.com session cookies</em>_, exactly as if you made the request yourself.<br>
Your browser just paid $1000 to the malicious attacker.<br>
And this could get much worse if the attacker can change the valid email or the password to your bank account website.</p>
</blockquote>
<blockquote>
<p>So in plain simple words this is how CSRF works. Always be careful how you handle your cookies. ;)</p>
</blockquote>

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTU2Nzg4NjA4N119
-->