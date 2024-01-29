# Cryptography

- formal security def:
- algo construction:
- math proof:


## topics

- symmetric key crypto
- asymmetric key crypto


## applications

- secure communication: in present tense or in future tense, **convert public open channel to secure channel**
    - ensuring privacy(data only with sender & receiver), authenticity(no MITM, confirm participating entities' identity), identity(tamper proof data)

### advanced application

- cryptocurrency
    - prevents **double spending while preserving anonymity**
- more fault tolerance/secret sharing among shareholders:
    - prevent single point of failure: distributed trust: 3-choose-2 key signing, the main key is deleted and the generated keys can sign/acheive the stuff over a distributed protocol
- Zero Knowledge Proofs/Proof of identity:
    - Sundarkand example: Ram sharing a proof(his ring, id-card/clear-text proof/fungible in today's world :| ) for Sita to believe Hanuman(the medium) & the message(letter), here the proof of msg source & the messenger authenticity is the **ring**, Sita is scared but trusts the proof, i.e. Ring and trusts the message & the messenger, messenger made a claim using the proof
    - ideally in real world(Z-knowledge) the details about the ring shouldn't be revealed and if Hanuman lacks the ring, the proof should be rejected
        - Alice: I know prime factors of N, Bob: Show the factors, A: I can proove without showing the factors ==> RSA public-key cryptosystem, pubKey(N) for encryption & p, q for decryption. N = p.q, where p,q are 512 byte primes; here p & q are the proof, Is N the zero knowledge proof????
- isomorphic graph: in absense of bijection/isomorphism, Alice can show that graphs are isomorphic without showing the bijection
- **outsource computation**/encrypted search: Google doesn't get to know what I searched but Google gave me the result, computationally weak client outsourcing the computation to server without revealing the underlying data/info, i.e. lack of **input/output privacy**, homomorphic encryption
- distributed consensus among mutually distrusting parties N parties & T corruptions
- secure multi-party communication(MPC): emulate the trusted third-party, inputs of individuals to remain a secret but the outcome is revealed to everyone, like election??


## Core problems

1. Key agreement: sender & receiver who have never met each other, need to talk to each other predictably(how to deal with imposters?) and over a public channel without letting others know
    - analogy: two kids shout information to each other and other peeps in the class can't figure a thing out :)
2. Secret Key K is exchanged and now have a common key, now they can communicate ensuring **confidentiality & integrity**

symmetric key primitive(private-key cryptography): sender & receiver have a pre-agreed key not known to adversary, computationally efficient,
asymmetric key primitive(public-key cryptography): different keys used at both ends, computationally inefficient by a few orders of magnitude,

- SSL uses the best of the both worlds

### Symmetric key encryption algo

1. GenerateKey() ➛ key k(output) ∈ 𝒦  (set of all possible outputs) --> takes no external input except **randomness**
    - 𝒦 --> set of all possible output keys of a particular bitsize

2. Encryption(plainText, key, randomness) ➛ ciphertext(one of the possible ciphertext sample from possible ciphertext superset), randomized algo; multiple runs of this algo will return a different value

3. Decryption(cipherText, key k) := plainText (one of the possible set of plainText superset); deterministic algo

- publicly known: gen fn, enc fn, dec fn
- not known publicly: secret-key k at places beyond the sender & receiver

#### Properties of a Secure Symmetric Encryption scheme

1. Correctness      : ∀ key k & message m Dec(Enc(m)) := m

2. Privacy(informal): by seeing the ciphertext, the adversary shouldn't compute anything about the plainText message m
    - slightly harder to define the above formally, because
        - cipherText doesn't reveal the **underlying key**: corollary: an enc algo where cipherText is same as plainText(there exist no key)
    - cipherText shouldn't reveal anything( **nothing should be revealed** ) **about the plainText**
        - not even 1% of the cipherText should be revealed!!
    - cipherText doesn't reveal any character of the underlying plainText
        - loophole: cipherText can reveal the range of the sensitive data
    - cipherText doesn't reveal any **meaningful info() about plainText**
    - cipherText doesn't help compute any function of the plainText
        - exactly cannot be formalized of cipherText's help to underlying fn,

    Attack Models
        - Ciphertext-only attack (COA): adversary knows the ciphertext only, passive nature, wants to compute some fn of plaintext
        - Known plaintext attack (KPA): adversary knows a bunch of cipherTxt & plainText, slightly more worrysome, "" --> explains why **Encryption algo should be randomized**, if the same msg is getting encrypted multiple times the fn can be guessed easily(Enigma movie)
        - Chosen plaintext attack (CPA): sort of MITM attack, adversary gets encryption oracle, i.e. can influence a party to encrypt a certain message m1 and reply back with c1 without the knowledge of sender/receiver within a practical amt of time to build a dictionary of ciphertext & plainText--> the attacker can also mutate the cipherText to understand how the response changes from other party, attack is active in nature, ""
        - Chosen ciphertext attack (CCA): two encryption oracles on both parties(i.e. encryption ^ decryption oracle), strongest possible attack,

3. Keys & Kerckhoff's Principle:
    - key should be a secret at all costs
    - a cryptosystem should be secure if everything about the system, except the key is public knowledge
        - key privacy is easier to maintain i.e. 100bits of magic, algo/program privacy is harder as it'll be 10^3 times larger
        - algo can be leaked/reverse-engineered
        - key can be replaced if the key is exposed
        - if algo is leaked, you are screwed
        - if the algo is public, it'd be under public scrutiny: well researched, etc _Trust my algorithm bro_ is not a good way to choose an algo, esp a private one
        - coming up with 100 secret algos for 100 pair of parties will be hard
