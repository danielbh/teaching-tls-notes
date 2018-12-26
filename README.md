Links:

https://blog.probely.com/how-to-deploy-modern-tls-in-2018-1b9a9cafc454


https://www.nginx.com/blog/nginx-https-101-ssl-basics-getting-started/#SSL

This is your SSL/TLS handshake. It’s a little complicated; there’s a lot of moving parts but essentially, if you take a step back it’s an extra one or two round trips between the client and the server that send cryptographic information. In this case, you have several options right here – there’s server randoms, there’s client randoms; this is all kind of deep stuff you don’t really need to know.

All you need to know is that the server itself sends a public key, and the client and server establish a shared secret that they can use to encrypt the communication. So, all the communication between the visitor and the server is encrypted with a symmetric key, meaning both parties have the same key. There’s also an integrity key, so in this case an HMAC, but I’ll skip over this diagram for now and go to the more salient question of “why set up HTTPS?”.
