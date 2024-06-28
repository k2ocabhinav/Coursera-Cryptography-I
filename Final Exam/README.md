## Question 1

*Let (E,D) be an authenticated encryption system built by combining a CPA-secure symmetric cipher and a MAC. The system is combined with an error-correction code to correct random transmission errors. In what order should encryption and error correction be applied?*  
1 / 1 point

- ❌ Apply the error correction code and then encrypt the result.
- ✅ Encrypt and then apply the error correction code.
- ❌ The order does not matter -- either one is fine.
- ❌ The order does not matter -- neither one can correct errors.

*That is correct. The error correction code will do its best to correct random errors after which the MAC in the ciphertext will be checked to ensure no other errors remain.*

---

## Question 2

*Let X be a uniform random variable over the set {0,1}^n. Let Y be an arbitrary random variable over the set {0,1}^n (not necessarily uniform) that is independent of X. Define the random variable Z = X ⊕ Y. What is the probability that Z equals 0^n?*  
1 / 1 point

- ✅ 1/2^n
- ❌ 1/n^2
- ❌ 2/2^n
- ❌ 1−(1/2^n)

*The probability is 1/2^n. To see why, observe that whatever Y is, the probability that Z = X ⊕ Y = 0^n is the same as the probability that X = Y which is exactly 1/2^n because X is uniform.*

---

## Question 3

*Suppose (E1,D1) is a symmetric cipher that uses 128-bit keys to encrypt 1024-bit messages. Suppose (E2,D2) is a symmetric cipher that uses 128-bit keys to encrypt 128-bit messages. The encryption algorithms E1 and E2 are deterministic and do not use nonces. Which of the following statements is true?*  
0 / 1 point

- ✅ (E1,D1) can be one-time semantically secure, but cannot be perfectly secure.
- ❌ (E1,D1) can be semantically secure under a chosen plaintext attack.
- ❌ (E2,D2) can be perfectly secure, but cannot be one-time semantically secure.
  - *This statement is incorrect: (E2,D2) can be the one-time pad which is both perfectly secure and one-time semantically secure.*
- ❌ (E2,D2) can be one-time semantically secure and perfectly secure.

*Yes, for example, (E1,D1) can be a secure stream cipher.*

---

## Question 4

*Which of the following statements regarding CBC and counter mode is correct?*  
1 / 1 point

- ✅ CBC mode encryption requires a block cipher (PRP), but counter mode encryption only needs a PRF.
- ❌ Both counter mode and CBC mode require a block cipher (PRP).
- ❌ Both counter mode and CBC mode can operate just using a PRF.
- ❌ Counter mode encryption requires a block cipher (PRP), but CBC mode encryption only needs a PRF.

*Yes, CBC needs to invert the PRP for decryption, while counter mode only needs to evaluate the PRF in the forward direction for both encryption and decryption. Therefore, a PRF is sufficient for counter mode.*

---

## Question 5

*Let G:X→X^2 be a secure PRG where X={0,1}^256. We let G(k)[0] denote the left half of the output and G(k)[1] denote the right half. Which of the following statements is true?*  
1 / 1 point

- ❌ F(k,m) = G(m)[0] ⊕ k is a secure PRF with key space and message space X.
- ❌ F(k,m) = G(k)[0] ⊕ m is a secure PRF with key space and message space X.
- ❌ F(k,m) = m ⊕ k is a secure PRF with key space and message space X.
- ✅ F(k,m) = G(k)[m] is a secure PRF with key space X and message space m ∈ {0,1}.

*Yes, since the output of G(k) is indistinguishable from random, the left and right halves are indistinguishable from random independent values.*

---

## Question 6

*Let (E,D) be a nonce-based symmetric encryption system (i.e. algorithm E takes as input a key, a message, and a nonce, and similarly the decryption algorithm takes a nonce as one of its inputs). The system provides chosen plaintext security (CPA-security) as long as the nonce never repeats. Suppose a single encryption key is used to encrypt 2^32 messages and the nonces are generated independently at random for each encryption, how long should the nonce be to ensure that it never repeats with high probability?*  
1 / 1 point

- ❌ 32 bits
- ❌ 16 bits
- ✅ 128 bits
- ❌ 64 bits

*Yes, the probability of repetition after 2^32 samples is negligible.*

---

## Question 7

*Same as question 6 except that now the nonce is generated using a counter. The counter resets to 0 when a new key is chosen and is incremented by 1 after every encryption. What is the shortest nonce possible to ensure that the nonce does not repeat when encrypting 2^32 messages using a single key?*  
1 / 1 point

- ✅ 32 bits
- ❌ 64 bits
- ❌ The nonce must be chosen at random, otherwise the system cannot be CPA secure.
- ❌ 16 bits

*Yes, with 32 bits there are 2^32 nonces and each message will use a different nonce.*

---

## Question 8

*Let (S,V) be a deterministic MAC system with message space M and key space K. Which of the following properties is implied by the standard MAC security definition?*  
0 / 1 point

- ❔ Given m and S(k,m) it is difficult to compute k.
- ❌ Given a key k in K it is difficult to find distinct messages m0 and m1 such that S(k,m0) = S(k,m1).
- ❔ S(k,m) preserves semantic security of m. That is, the adversary learns nothing about m given S(k,m).
- ❔ The function S(k,m) is a secure PRF.

*No, there are secure MACs where this is easy. If the attacker has the key k the MAC has no security.*

---

## Question 9

*Let H:M→T be a collision-resistant hash function where |T| is smaller than |M|. Which of the following properties is implied by collision resistance?*  
1 / 1 point

- ❌ It is difficult to find m0 and m1 such that H(m0) = H(m1) + 1. (Here we treat the outputs of H as integers)
- ✅ Given a tag t ∈ T it is difficult to construct m ∈ M such that H(m) = t.
- ❌ H(m) preserves semantic security of m (that is, given H(m) the attacker learns nothing about m).
- ❌ For all m in M, H(m) must be shorter than m.

*Yes, if these were easy then the attacker could easily find collisions.*

---

## Question 10

*Recall that when encrypting data you should typically use a symmetric encryption system that provides authenticated encryption. Let (E,D) be a symmetric encryption system providing authenticated encryption. Which of the following statements is implied by authenticated encryption?*  
1 / 1 point

- ❌ Given k, m, and E(k,m) the attacker cannot create a valid encryption of m + 1 under key k. (Here we treat plaintexts as integers)
- ✅ Given m and E(k,m) it is difficult to find k.
- ❌ The attacker cannot create a ciphertext c such that D(k,c) = ⊥.
- ✅ Given m and E(k,m) the attacker cannot create a valid encryption of m + 1. (Here we treat plaintexts as integers)

*Yes, otherwise the system would not even be chosen plaintext secure. Yes, otherwise the system would not have ciphertext integrity.*

---

## Question 11

*Which of the following statements is true about the basic Diffie-Hellman key-exchange protocol?*  
1 / 1 point

- ❌ As with RSA, the protocol only provides eavesdropping security in the group ZN* where N is an RSA modulus.
- ✅ The basic protocol enables key exchange secure against eavesdropping, but is insecure against active adversaries that can inject and modify messages.
- ✅ The protocol can be converted to a public-key encryption system called the ElGamal public-key system.
- ❌ The protocol is based on the concept of

 a trapdoor function.

*Yes, Diffie-Hellman is secure against eavesdropping, but is insecure against man-in-the-middle attacks. Yes, that is correct.*

---

## Question 12

*Suppose n + 1 parties, call them B, A1,…, An, wish to set up a shared group key. They want a protocol so that at the end of the protocol they all have a common secret key k, but an eavesdropper who sees the entire conversation cannot determine k. The parties agree on the following protocol that runs in a group G of prime order q with generator g:*

1. *For i = 1,…,n party Ai chooses a random ai in {1,…,q} and sends to Party B the quantity Xi ← g^ai.*
2. *Party B generates a random b in {1,…,q} and for i = 1,…,n responds to Party Ai with the messages Yi ← Xib.*

*The final group key should be g^b. Clearly Party B can compute this group key. How would each Party Ai compute this group key?*  
1 / 1 point

- ❌ Party Ai computes g^b as Yi^ai.
- ❌ Party Ai computes g^b as Yi^(-ai).
- ✅ Party Ai computes g^b as Yi^(1/ai).
- ❌ Party Ai computes g^b as Yi^(-1/ai).

*Yes, Yi^(1/ai) = g^(bai)/ai = g^b.*

---

## Question 13

*Recall that the RSA trapdoor permutation is defined in the group ZN* where N is a product of two large primes. The public key is (N,e) and the private key is (N,d) where d is the inverse of e in Zφ(N)*. Suppose RSA was defined modulo a prime p instead of an RSA composite N. Show that in that case anyone can compute the private key (N,d) from the public key (N,e) by computing:*  
1 / 1 point

- ✅ d ← e^(-1) (mod p - 1)
- ❌ d ← e^(-1) (mod p)
- ❌ d ← -e (mod p)
- ❌ d ← e^(-1) (mod p + 1)

*Yes, that is correct.*