# Perfect Security

- always desirable, but comes with a heavy price
    - key as long as message
    - fresh key for each encryption
- _sort of impractical_ ^^

- modern cryptography:
- what? : the cipher C should leak no additional info about the plainText other than any prior info the attacker already knows
- what formally? : (no additional info) probab that m has been communicated by sender
- Attack model: ciphertext only attack
- assumption: adversary has infinite computation i.e. computationally unbounded
- irrespective of any prior info the attacker has about the plainTextMessage the ciphertext C should not leak any info about the plainText

- Π(Gen, Enc, Dec) a publicly known cipher
    - most algos produce a Key as a uniform distribution, i.e. each Key K is equally likely
    - the adversary knows the probability of the Gen, Enc & Dec functions
    - the adversary can take a guess of the message in plainText
    - Pr[𝐊 = k] : probablility that Gen gives a key k is 1/|𝒦 | where 𝒦  is the set of keys Gen() can give
    - Pr[𝐌 = m] : "", plainText message, probablility distribution over the message space
    - Pr[𝐂 = c] : "", cipherText message, "" over the cipher space
    - M, K are independent of each other, C depends on M & K

- adversary knowing the enc & dec algo can compute an encryption matrix where plainText & cipherTexts are part of cols

- Perfect security original definition:
    - below cond should hold for every probab distribution over M & K, over every m ∈ M & every c ∈ C
    - Pr[𝐌  = m |𝐂 = c] = Pr[𝐌 = m] `<--- by Shanon`
    - (informal definition) attacker should not get more info(additional info) about the plainText by looking at cipherText
    - RHS = message m could be communicated by sender when keygen has not happened and encryption has not happened(a-priori probab that m might be communicated)
    - LHS = posteriori probablity that message m is encrypted in c
    - i.e. **by looking at C does not make attacker's knowledge about the plainText m** and that holds even if **adversary is computationally unbounded**


    - interpretation of original def: probab of knowing plainText m remains the same before and after seeing the cipherText
    - alt def: for every probab distribution over M & K, the probab of m0 or m1 can be c0 should be same, i.e. no bias in probab for enc of m0 or m1
        - Pr[𝐂 = c | 𝐌 = m0 ] = Pr[𝐂 = c | 𝐌 = m1]

#### Proof of Def1

- assume that the alt def is true
- https://www.khanacademy.org/math/statistics-probability/probability-library
