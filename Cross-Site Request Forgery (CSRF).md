


># Cross-Site Request Forgery (CSRF)

> Some times when i am reading a technical article or trying to understand a technical concept, i always which someone could explain to me like i am a 5 year old.
>So in the same spirit i am going to try explain CSRF like am explaining to a 5 year old.

> Imagine that i am a regular customer to a candy store and the entry to the candy store can only be granted if you know the secret phrase that you need to tell the guard of the candy store.
> Now lets say a bad kid x not only tricks you to reveal the secret phrase but also does a good job of impersonating you. The candy store guard has no way to know if its you or the bad kid x ask to get in the candy store.

>This is exactly what happens  with CSRF.  The candy  store can be your bank, the malicious attacker is the bad kid x and the secret phrase is your username and password for the bank website.

> The malicious attacker will send a an HTML e-mail including something like the following tag

    <img src="https://www.bank.com/transfer?amount=1000&amp;destination=malicious -attacker">

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTI2MTIxOTMyMl19
-->