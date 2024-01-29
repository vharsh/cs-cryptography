# History

- Shift Cipher, e.g. Caesar(shift each plain text char by k chars fwd/bck) & Vigenere cipher
    - Caesar:  𝒦 = { 0, 1, 2, ... 25 } M = C = set of strings {0, ... 25}
        - C = (mᵢ+ k) % 26
        - D = (cᵢ- k) & 26
        - brute force & dictionary attack is possible
        - lesson learnt: sufficient key space principle, a cipher must have a key-space that's not vulnerable to exhaustive search
    - mono-alphabetic substitution cipher:
        - makes brute force attack harder, due to larger candidate key space, 26! = 2⁸⁸
        - frequency analysis due to redundancy of each characters i.e. monogram(e), bigram(an, th), trigram(the)
    - Poly-Alphabetic substitution Cipher(Vigenere)
        - multiple instances of shift cipher, each plainText character is mapped to different cipherText character
        - key generation algo selects a different length of the shift-key each time
        - each block of the data is shifted by a block of the shift-key
        - cryptanalysis: two stage approach, 1) determine the size of the shift-key (Kasiski's method & index of coincidence method) 2) try to determine the characters k1, k2..kt of the key k ( TODO: go over this again )
