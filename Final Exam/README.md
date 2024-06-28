1.
Question 1

Let (E,D)(E,D) be an authenticated encryption system built by combining

a CPA-secure symmetric cipher and a MAC.    The system is combined

with an error-correction code to correct random transmission errors.

In what order should encryption and error correction be applied?
1 / 1 point

The order does not matter -- neither one can correct errors. 

Apply the error correction code and then encrypt the result.

Encrypt and then apply the error correction code.

The order does not matter -- either one is fine.
Correct

 That is correct.  The error correction code will do its best 

to correct random errors after which the MAC in the ciphertext will be checked

to ensure no other errors remains.
2.
Question 2

Let XX be a uniform random variable over the set {0,1}n{0,1}n.

Let YY be an arbitrary random variable over the set {0,1}n{0,1}n (not

necessarily uniform) that is independent of XX.

Define the random variable Z=X⊕YZ=X⊕Y.    What is the probability

that ZZ equals 0n0n?
1 / 1 point

 11

 0.50.5

 1/2n1/2n

1−(1/2n)1−(1/2n)
Correct

The probability is 1/2n1/2n.  To see why, observe

that whatever YY is, the probability that 

Z=X⊕Y=0nZ=X⊕Y=0n is the same as the probability that X=YX=Y which is

exactly 1/2n1/2n because XX is uniform. 
3.
Question 3

Suppose (E1,D1)(E1​,D1​) is a symmetric cipher that uses 128 bit keys to

encrypt 1024 bit messages.  Suppose (E2,D2)(E2​,D2​) is a symmetric

cipher that uses 128 bit keys to encrypt 128 bit messages.  

The encryption algorithms E1E1​ and E2E2​ are deterministic and

do not use nonces.   Which of the following statements is true?
1 / 1 point

(E1,D1)(E1​,D1​) can be one-time semantically secure, but cannot be perfectly 

secure.
Correct

Yes, for example (E1,D1)(E1​,D1​) can be a secure stream cipher.

(E2,D2)(E2​,D2​) can be semantically secure under a chosen plaintext attack.

(E1,D1)(E1​,D1​) can be perfectly secure.

(E1,D1)(E1​,D1​) can be one-time semantically secure.
Correct

Yes, for example (E1,D1)(E1​,D1​) can be a secure stream cipher.
4.
Question 4

Which of the following statements regarding CBC and counter mode is correct?
1 / 1 point

counter mode encryption requires a block

cipher (PRP), but CBC mode encryption only needs a PRF.

Both counter mode and CBC mode require a block

cipher (PRP).

 Both counter mode and CBC mode can operate

just using a PRF. 

 CBC mode encryption requires a block

cipher (PRP), but counter mode encryption only needs a PRF.
Correct

 Yes, CBC needs to invert the PRP for decryption, while 

counter mode only needs to evaluate the PRF in the forward direction

for both encryption and decryption.     Therefore, a PRF is 

sufficient for counter mode.
5.
Question 5

Let G:X→X2G:X→X2 be a secure PRG where X={0,1}256X={0,1}256.   

We let G(k)[0]G(k)[0] denote

the left half of the output and G(k)[1]G(k)[1] denote the right half.

Which of the following statements is true?
1 / 1 point

F(k,m)=G(m)[0]⊕kF(k,m)=G(m)[0]⊕k is a secure PRF with key space and message 

space XX.

F(k,m)=G(k)[m]F(k,m)=G(k)[m] is a secure PRF with key space XX and message

space m∈{0,1}m∈{0,1}.

F(k,m)=m⊕kF(k,m)=m⊕k is a secure PRF with key space and message space XX.

F(k,m)=G(k)[0]⊕mF(k,m)=G(k)[0]⊕m is a secure PRF with key space and message 

space XX.
Correct

Yes, since the output of G(k)G(k) is indistinguishable from

random, the left and right halves are indistinguishable from random

independent values.
6.
Question 6

Let (E,D)(E,D) be a nonce-based symmetric encryption system (i.e. algorithm

EE takes as input a key, a message, and a nonce, and similarly the

decryption algorithm takes a nonce as one of its inputs).   The system

provides chosen plaintext security (CPA-security) as long as the nonce

never repeats.   Suppose a single encryption key is used to encrypt

232232 messages and the nonces are generated independently at random for each

encryption, how long should the nonce be to ensure that it never repeats

with high probability?
1 / 1 point

16 bits

64 bits

128 bits

32 bits
Correct

 Yes, the probability of repetition after 232232 samples

is negligible.
7.
Question 7

Same as question 6 except that now the nonce is generated using a counter.  The counter resets to 0 when a new key is chosen and is incremented by 1 after every encryption.   What is the shortest nonce possible to ensure that the nonce does not repeat when encrypting 232232 messages using a single key?
1 / 1 point

 32 bits

 16 bits

the nonce must be chosen at random, otherwise the system

cannot be CPA secure.

48 bits
Correct

Yes, with 32 bits there are 232232 nonces and each

message will use a different nonce. 
8.
Question 8

Let (S,V)(S,V) be a deterministic MAC system with message space MM and key 

space KK.   Which of the following properties is implied by the 

standard MAC security definition?
0 / 1 point

S(k,m)S(k,m) preserves semantic security of mm.

That is, the adversary learns nothing about mm given S(k,m)S(k,m).

Given mm and S(k,m)S(k,m) it is difficult to compute kk.

Given a key kk in KK it is difficult to find

distinct messages m0m0​ and m1m1​ such that S(k,m0)=S(k,m1)S(k,m0​)=S(k,m1​).  

 The function S(k,m)S(k,m) is a secure PRF.
Incorrect

no, S(k,m)=(m, HMAC(k,m))S(k,m)=(m, HMAC(k,m)) is a secure MAC, but does nothing to hide mm.
9.
Question 9

Let H:M→TH:M→T be a collision resistant hash function where ∣T∣∣T∣ is smaller than ∣M∣∣M∣.

Which of the following properties is implied by collision resistance?
0 / 1 point

It is difficult to construct two distinct messages

m0m0​ and m1m1​ such that H(m0)=H(m1)H(m0​)=H(m1​).

 it is difficult to find m0m0​ and m1m1​ such

that H(m0)=H(m1)+1H(m0​)=H(m1​)+1.   (here we treat the outputs of HH as integers)

 H(m)H(m) preserves semantic security of mm

(that is, given H(m)H(m) the attacker learns nothing about mm).

For all mm in MM, H(m)H(m) must be shorter than mm.    
Incorrect

no, for example H(m)=mH(m)=m is collision resistance, but

does not hide mm.
10.
Question 10

Recall that when encrypting data you should typically use

a symmetric encryption system that provides authenticated encryption.

Let (E,D)(E,D) be a symmetric encryption system providing authenticated

encryption.   Which of the following statements is implied by

authenticated encryption?
1 / 1 point

 The attacker cannot create a ciphertext cc

such that D(k,c)=⊥D(k,c)=⊥.

Given mm and E(k,m)E(k,m) it is difficult to find kk.
Correct

yes, otherwise the system would not even be chosen plaintext

secure.

Given mm and E(k,m)E(k,m) the attacker

cannot create a valid encryption of m+1m+1.   (here we treat plaintexts

as integers)
Correct

 yes, otherwise the system would not have ciphertext

integrity.

Given k,mk,m and E(k,m)E(k,m) the attacker

cannot create a valid encryption of m+1m+1 under key kk.   

(here we treat plaintexts as integers)
11.
Question 11

Which of the following statements is true about the basic Diffie-Hellman

key-exchange protocol.
1 / 1 point

 As with RSA, the protocol only provides

eavesdropping security in the group ZN∗ZN∗​ where NN is an 

RSA modulus.

The protocol can be converted to a public-key

encryption system called the ElGamal public-key system. 
Correct

yes, that is correct.

The basic protocol enables key exchange secure against

eavesdropping, but is insecure against active adversaries that can

inject and modify messages. 
Correct

yes, Diffie-Hellman is secure against eavesdropping,

but is insecure against man in the middle attacks. 

The protocol is based on the concept of a trapdoor

function.
12.
Question 12

Suppose n+1n+1 parties, call them B,A1,…,AnB,A1​,…,An​, wish to setup

a shared group key.    They want a protocol so that at the end

of the protocol they all have a common secret key kk, but an eavesdropper

who sees the entire conversation cannot determine kk.   The parties

agree on the following protocol that runs in a group GG of prime order qq

with generator gg:

    for i=1,…,ni=1,…,n party AiAi​ chooses a random aiai​ in {1,…,q}{1,…,q} and sends to Party BB the quantity Xi←gaiXi​←gai​.

    Party BB generates a random bb in {1,…,q}{1,…,q} and for i=1,…,ni=1,…,n responds to Party AiAi​ with the messages Yi←XibYi​←Xib​.

The final group key should be gbgb.   Clearly Party BB can compute

this group key.   How would each Party AiAi​ compute this group key?
1 / 1 point

Party AiAi​ computes gbgb as Yi1/aiYi1/ai​​

 Party AiAi​ computes gbgb as Yi−aiYi−ai​​

Party AiAi​ computes gbgb as YiaiYiai​​

 Party AiAi​ computes gbgb as Yi−1/aiYi−1/ai​​
Correct

Yes,  Yi1/ai=g(bai)/ai=gbYi1/ai​​=g(bai​)/ai​=gb.
13.
Question 13

Recall that the RSA trapdoor permutation is defined in the group 

ZN∗ZN∗​ where NN is a product of two large

primes.   The public key is (N,e)(N,e) and the private key is (N,d)(N,d) 

where dd is the inverse of ee in Zφ(N)∗Zφ(N)∗​.   

Suppose RSA was defined modulo a prime pp instead of an RSA 

composite NN.  Show that in that case anyone can compute the private 

key (N,d)(N,d) from the public key (N,e)(N,e) by computing:
1 / 1 point

d←e−1 (modp+1)d←e−1 (modp+1).

 d←e−1 (modp−1)d←e−1 (modp−1).

d←−e (modp)d←−e (modp).

d←e−1 (modp2)d←e−1 (modp2).
Correct

yes, that is correct.