Links:

https://blog.probely.com/how-to-deploy-modern-tls-in-2018-1b9a9cafc454

TLS is a protocol that provides a way for two parties to establish a secure communication channel between them.

That’s it.

But keep in mind that achieving this is no small feat. Look at TLS’ vulnerability history to see how hard it is.

TLS makes establishing a secure communication channel possible by providing three key services:

Confidentiality: ensures that data exchanged between peers is kept secret from third-parties. This is especially important for sensitive data, like passwords, credit cards, and the embarrassing contents of our shopping carts. Confidentiality is the characteristic that is most commonly associated with TLS, and its purpose is usually well understood;
    
Integrity: makes sure that data transmitted between peers is reliable and not tampered with during transit. Note that in the context of TLS, “integrity” refers to message authentication;
    
Authentication: ensures that clients communicate with legitimate servers. This is fundamental for assuring both confidentiality, and integrity, by providing trustworthy keying material for encryption and message authentication. Note that authentication and integrity are always important, whether the transmitted data is confidential or not. Optionally, TLS can also be used to authenticate clients, e.g. through client certificates, but this is less common;


https://www.nginx.com/blog/nginx-https-101-ssl-basics-getting-started/#SSL

This is your SSL/TLS handshake. It’s a little complicated; there’s a lot of moving parts but essentially, if you take a step back it’s an extra one or two round trips between the client and the server that send cryptographic information. In this case, you have several options right here – there’s server randoms, there’s client randoms; this is all kind of deep stuff you don’t really need to know.

All you need to know is that the server itself sends a public key, and the client and server establish a shared secret that they can use to encrypt the communication. So, all the communication between the visitor and the server is encrypted with a symmetric key, meaning both parties have the same key. There’s also an integrity key, so in this case an HMAC, but I’ll skip over this diagram for now and go to the more salient question of “why set up HTTPS?”.

https://blog.cloudflare.com/tls-1-3-overview-and-q-and-a/
https://blog.cloudflare.com/rfc-8446-aka-tls-1-3/
