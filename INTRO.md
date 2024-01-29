# Cryptography is everywhere

- secure communications
    - e.g. HTTPS(actually SSL/TLS), no eavesdropping/tampering
    - two parts
        - handshake protocol: establish shared secret keys using Public-Key crypto[course#2]
        - record layer: transmit data using shared secret key[course#1]
- encrypting files on disk
    - e.g. file on disk over ZFS(say), no eavesdropping/tampering: _Alice today_ communicating with _Alice tomorrow_
- content protection: DVD(CSS, easy to break), Blu-Ray(AACS)
- user authentication

# symmetric encryption: building block for securing traffic

Alice & Bob has a shared secret key from a public algo
E(k,msg) = cypher
D(k,cypher) = msg

- the symmetric key can be **single use(one-time-key) or multi-use(many time key)**
