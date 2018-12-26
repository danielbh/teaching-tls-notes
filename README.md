Links:

https://blog.probely.com/how-to-deploy-modern-tls-in-2018-1b9a9cafc454

TLS is a protocol that provides a way for two parties to establish a secure communication channel between them.

That’s it.

But keep in mind that achieving this is no small feat. Look at TLS’ vulnerability history to see how hard it is.

TLS makes establishing a secure communication channel possible by providing three key services:

Confidentiality: ensures that data exchanged between peers is kept secret from third-parties. This is especially important for sensitive data, like passwords, credit cards, and the embarrassing contents of our shopping carts. Confidentiality is the characteristic that is most commonly associated with TLS, and its purpose is usually well understood;
    
Integrity: makes sure that data transmitted between peers is reliable and not tampered with during transit. Note that in the context of TLS, “integrity” refers to message authentication;
    
Authentication: ensures that clients communicate with legitimate servers. This is fundamental for assuring both confidentiality, and integrity, by providing trustworthy keying material for encryption and message authentication. Note that authentication and integrity are always important, whether the transmitted data is confidential or not. Optionally, TLS can also be used to authenticate clients, e.g. through client certificates, but this is less common;

 OpenSSL and nginx a few months ago. Be aware that, if you are using OpenSSL ≥ 1.1 with nginx stable (1.14 at this time), you are still vulnerable. 


https://www.nginx.com/blog/nginx-https-101-ssl-basics-getting-started/#SSL

This is your SSL/TLS handshake. It’s a little complicated; there’s a lot of moving parts but essentially, if you take a step back it’s an extra one or two round trips between the client and the server that send cryptographic information. In this case, you have several options right here – there’s server randoms, there’s client randoms; this is all kind of deep stuff you don’t really need to know.

All you need to know is that the server itself sends a public key, and the client and server establish a shared secret that they can use to encrypt the communication. So, all the communication between the visitor and the server is encrypted with a symmetric key, meaning both parties have the same key. There’s also an integrity key, so in this case an HMAC, but I’ll skip over this diagram for now and go to the more salient question of “why set up HTTPS?”.

https://blog.cloudflare.com/tls-1-3-overview-and-q-and-a/
https://blog.cloudflare.com/rfc-8446-aka-tls-1-3/

For the last five years, the Internet Engineering Task Force (IETF), the standards body that defines internet protocols, has been working on standardizing the latest version of one of its most important security protocols: Transport Layer Security (TLS). TLS is used to secure the web (and much more!), providing encryption and ensuring the authenticity of every HTTPS website and API. The latest version of TLS, TLS 1.3 (RFC 8446) was published today. It is the first major overhaul of the protocol, bringing significant security and performance improvements. This article provides a deep dive into the changes introduced in TLS 1.3 and its impact on the future of internet security.

Serving your content over HTTPS instead of HTTP provides confidence to the visitor that the content they see is presented by the legitimate content owner and that the communication is safe from eavesdropping. This is a big deal in a world where online privacy is more important than ever.

Many people still refer to web encryption as SSL, even though the vast majority of services have switched over to supporting TLS only. The term SSL continues to have popular appeal and Cloudflare has kept the term alive through product names like Keyless SSL and Universal SSL.

https://www.globalsign.com/en/blog/ssl-vs-tls-difference/

Both SSL 2.0 and 3.0 have been deprecated by the IETF (in 2011 and 2015, respectively). Over the years vulnerabilities have been and continue to be discovered in the deprecated SSL protocols (e.g. POODLE, DROWN). Most modern browsers will show a degraded user experience (e.g. line through the padlock or https in the URL bar, security warnings) when they encounter a web server using the old protocols. For these reasons, you should disable SSL 2.0 and 3.0 in your server configuration, leaving only TLS protocols enabled.

Before anyone starts worrying that they need to replace their existing SSL Certificates with TLS Certificates, it’s important to note that certificates are not dependent on protocols. That is, you don’t need to use a TLS Certificate vs. an SSL Certificate. While many vendors tend to use the phrase “SSL/TLS Certificate”, it may be more accurate to call them “Certificates for use with SSL and TLS", since the protocols are determined by your server configuration, not the certificates themselves.

It’s worth noting here that SSL and TLS simply refer to the handshake that takes place between a client and a server. The handshake doesn’t actually do any encryption itself, it just agrees on a shared secret and type of encryption that is going to be used.

https://security.stackexchange.com/questions/5126/whats-the-difference-between-ssl-tls-and-https
