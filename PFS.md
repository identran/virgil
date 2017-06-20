# Perfect Forward Secrecy

The security of communications transmitted across the Internet can be improved with public key cryptography. However, if the public and private keys used in those communications are compromised, so is the data exchanged in that session (as well as the data exchanged in previous sessions).

Perfect Forward Secrecy (PFS) is a technique that protects previously intercepted traffic from being decrypted, even if the main private key is compromised. With PFS enabled communication, a hacker could only access information that is actively transmitted. This is because PFS forces a system to create a different key every session. In other words, PFS guarantees that there is no master key capable of decrypting all of the information traffic.

In PFS, you utilize Diffie-Hellman key exchange algorithms, where the master key is only used to set the parameters. After the parameters for the algorithm are agreed on, the key exchange takes place, and a new secret key is generated for both parties. The parameters are not secret, and the secret keys used by both parties are discarded after the session key is established. This way, even if somebody discovers the master key, they cannot discover the session key.

![PFS](https://github.com/VirgilSecurity/virgil/blob/master/images/PFS.png)



### Bob side (receiver)
Before Bob can use PFS, he must do the following:

1. Have a main key pair (identity)
2. Generate an ephemeral key pair, then sign it with the main key


### Alice side (sender)

1. Have a main key pair (her identity)
2. Generate an ephemeral key pair, then sign it with the main key
3. Get Bob's identity, via his ephemeral public key

### Conclusion

PFS is critical for dealing with sensitive data because it adds an extra layer of security. With PFS, the session key is derived from the input of both parties and is never transmitted through the Internet. Furthermore, it is freshly generated for each session.
