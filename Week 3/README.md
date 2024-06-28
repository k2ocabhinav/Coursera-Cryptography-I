# Cryptography I 
# Week 3 - Problem Set

## Question 1

*Suppose a MAC system (S,V) is used to protect files in a file system by appending a MAC tag to each file. The MAC signing algorithm S is applied to the file contents and nothing else. What tampering attacks are not prevented by this system?*

- ✅ Changing the name of a file.
- ❌ Changing the first byte of the file contents.
- ❌ Appending data to a file.
- ❌ Replacing the contents of a file with the concatenation of two files on the file system.

  *The MAC signing algorithm is only applied to the file contents and does not protect the file name.*

## Question 2

*Let (S,V) be a secure MAC defined over (K,M,T) where M={0,1}^n and T={0,1}^128. That is, the key space is K, message space is {0,1}^n, and tag space is {0,1}^128. Which of the following is a secure MAC: (as usual, we use ∥ to denote string concatenation)*

- ✅ S′(k,m)=S(k,m)[0,…,126] and V′(k,m,t)=[V(k, m, t∥0)  or  V(k, m, t∥1)] (i.e., V′(k,m,t) outputs "1" if either t∥0 or t∥1 is a valid tag for m)
  - *A forger for (S′,V′) gives a forger for (S,V).*
- ❌ S′(k,m)={S(k,1^n) if m=0^n S(k,m) otherwise and V′(k,m)={V(k,1^n,t) if m=0^n V(k,m,t) otherwise}
- ❌ S′(k,m)=S(k,m) and V′(k,m,t)={V(k,m,t) if m≠0^n “1” otherwise}
- ❌ S′(k,m)=S(k,m⊕m) and V′(k,m,t)=V(k, m⊕m, t)
- ✅ S′(k, m)=[t←S(k,m), output (t,t) ] and V′(k,m,(t1,t2))={V(k,m,t1) if t1=t2 "0" otherwise (i.e., V′(k,m,(t1,t2)) only outputs "1" if t1 and t2 are equal and valid)}
  - *A forger for (S′,V′) gives a forger for (S,V).*
- ✅ S′(k,m)=S(k,m⊕1^n) and V′(k,m,t)=V(k,m⊕1^n,t)
  - *A forger for (S′,V′) gives a forger for (S,V).*

## Question 3

*Recall that the ECBC-MAC uses a fixed IV (in the lecture we simply set the IV to 0). Suppose instead we chose a random IV for every message being signed and include the IV in the tag. In other words, S(k,m):=(r, ECBCr(k,m)) where ECBCr(k,m) refers to the ECBC function using r as the IV. The verification algorithm V given key k, message m, and tag (r,t) outputs "1" if t=ECBCr(k,m) and outputs "0" otherwise. The resulting MAC system is insecure. An attacker can query for the tag of the 1-block message m and obtain the tag (r,t). He can then generate the following existential forgery: (we assume that the underlying block cipher operates on n-bit blocks)*

- ❌ The tag (r⊕1^n, t) is a valid tag for the 1-block message m⊕1^n.
- ❌ The tag (r, t⊕r) is a valid tag for the 1-block message 0^n.
- ❌ The tag (r⊕t, m) is a valid tag for the 1-block message 0^n.
- ✅ The tag (m⊕t, t) is a valid tag for the 1-block message 0^n.

  *The right half of the tag, m, is not likely to be the result of the CBC MAC.*

## Question 4

*Suppose Alice is broadcasting packets to 6 recipients B1,…,B6. Privacy is not important but integrity is. In other words, each of B1,…,B6 should be assured that the packets he is receiving were sent by Alice. Alice decides to use a MAC. Suppose Alice and B1,…,B6 all share a secret key k. Alice computes a tag for every packet she sends using key k. Each user Bi verifies the tag when receiving the packet and drops the packet if the tag is invalid. Alice notices that this scheme is insecure because user B1 can use the key k to send packets with a valid tag to users B2,…,B6 and they will all be fooled into thinking that these packets are from Alice. Instead, Alice sets up a set of 4 secret keys S={k1,…,k4}. She gives each user Bi some subset Si⊆S of the keys. When Alice transmits a packet she appends 4 tags to it by computing the tag with each of her 4 keys. When user Bi receives a packet he accepts it as valid only if all tags corresponding to his keys in Si are valid. For example, if user B1 is given keys {k1,k2} he will accept an incoming packet only if the first and second tags are valid. Note that B1 cannot validate the 3rd and 4th tags because he does not have k3 or k4. How should Alice assign keys to the 6 users so that no single user can forge packets on behalf of Alice and fool some other user?*

- ✅ S1={k2,k4}, S2={k2,k3}, S3={k3,k4}, S4={k1,k3}, S5={k1,k2}, S6={k1,k4}
  - *Every user can only generate tags with the two keys he has. Since no set Si is contained in another set Sj, no user i can fool a user j into accepting a message sent by i.*

- ❌ S1={k1,k2}, S2={k1}, S3={k1,k4}, S4={k2,k3}, S5={k2,k4}, S6={k3,k4}
- ❌ S1={k1,k2}, S2={k1,k3}, S3={k1,k4}, S4={k2,k3}, S5={k2,k4}, S6={k4}
- ❌ S1={k1,k2}, S2={k2,k3}, S3={k3,k4}, S4={k1,k3}, S5={k1,k2}, S6={k1,k4}

## Question 5

*Consider the encrypted CBC MAC built from AES. Suppose we compute the tag for a long message m comprising of n AES blocks. Let m′ be the n-block message obtained from m by flipping the last bit of m (i.e. if the last bit of m is b then the last bit of m′ is b⊕1). How many calls to AES would it take to compute the tag for m′ from the tag for m and the MAC key? (in this question please ignore message padding and simply assume that the message length is always a multiple of the AES block size)*

- ❌ 6
- ❌ n
- ❌ 4
- ✅ 5

  *You would decrypt the final CBC MAC encryption step done using k2, then decrypt the last CBC MAC encryption step done using k1, flip the last bit of the result, and re-apply the two encryptions.*

## Question 6

*Let H:M→T be a collision-resistant hash function. Which of the following is collision-resistant: (as usual, we use ∥ to denote string concatenation)*

- ✅ H′(m)=H(H(H(m)))
  - *A collision finder for H′ gives a collision finder for H.*
- ❌ H′(m)=H(0)
- ❌ H′(m)=H(m)⊕H(m)
- ❌ H′(m)=H(m)[0,…,31] (i.e., output the first 32 bits of the hash)
- ❌ H′(m)=H(m)⨁H(m⊕1∣m∣) (where m⊕1∣m∣ is the complement of m)
- ✅ H′(m)=H(H(m))
  - *A collision finder for H′ gives a collision finder for H.*
- ✅ H′(m)=H(m)∥H(m)
  - *A collision finder for H′ gives a collision finder for H.*

## Question 7

*Suppose H1 and H2 are collision-resistant hash functions mapping inputs in a set M to {0,1}^256. Our goal is to show that the function H2(H1(m)) is also collision-resistant. We prove the contra-positive: suppose H2(H1(⋅)) is not collision-resistant, that is, we are given x≠y such that H2(H1(x))=H2(H1(y)). We build a collision for either H1 or for H2. This will prove that if H1 and H2 are collision-resistant then so is H2(H1(⋅)). Which of the following must be true:*

- ✅ Either x,y are a collision for H2 or H1(x),H1(y) are a collision for H1.
  - *If H2(H1(x))=H2(H1(y)) then either H1(x)=H1(y) and x≠y, thereby giving us a collision on H1. Or H1(x)≠H1(y) but H2(H1(x))=H2(H1(y)) giving us a collision on H2. Either way, we obtain a collision on H1 or H2 as required.*
- ❌ Either x,y are a collision for H1 or H1(x),H1(y) are a collision for H2.
- ❌ Either H2(x),H2(y) are a collision for H1 or x,y are a collision for H2.
- ❌ Either x,y are a collision for H1 or x,y are a collision for H2.

## Question 8

*In this question, you are asked to find a collision for the compression function: f1(x,y)=AES(y,x)⨁y, where AES(x,y) is the AES-128 encryption of y under key x. Your goal is to find two distinct pairs (x1,y1) and (x2,y2) such that f1(x1,y1)=f1(x2,y2). Which of the following methods finds the required (x1,y1) and (x2,y2)?*

- ❌ Choose x1,y1,y2 arbitrarily (with y1≠y2) and let v:=AES(y1,x1). Set x2=AES−1(y2, v⊕y2).
- ❌ Choose x1,y1,x2 arbitrarily (with x1≠x2) and let v:=AES(y1,x1). Set y2=AES−1(x2, v⊕y1⊕x2).
- ❌ Choose x1,y1,y2 arbitrarily (with y1≠y2) and let v:=AES(y1,x1). Set x2=AES−1(y2, v⊕y1⊕y2).
- ✅ Choose x1,y1,y2 arbitrarily (with y1≠y2) and let v:=AES(y1,x1). Set x2=AES−1(y2, v⊕y1).

  *You got it!*

## Question 9

*Repeat the previous question, but now to find a collision for the compression function f2(x,y)=AES(x,x)⨁y. Which of the following methods finds the required (x1,y1) and (x2,y2)?*

- ❌ Choose x1,x2,y1 arbitrarily (with x1≠x2) and set y2=AES(x1,x1)⊕AES(x2,x2).
- ❌ Choose x1,x2,y1 arbitrarily (with x1≠x2) and set y2=y1⊕AES(x1,x1)⊕AES(x2,x2).
- ❌ Choose x1,x2,y1 arbitrarily (with x1≠x2) and set y2=y1⊕x1⊕AES(x2,x2).
- ✅ Choose x1,x2,y1 arbitrarily (with x1≠x2) and set y2=y1⊕AES(x1,x1).

  *Awesome!*

## Question 10

*Let H:M→T be a random hash function where ∣M∣≫∣T∣ (i.e. the size of M is much larger than the size of T). In lecture we showed that finding a collision on H can be done with O(∣T∣^1/2) random samples of H. How many random samples would it take until we obtain a three-way collision, namely distinct strings x,y,z in M such that H(x)=H(y)=H(z)?*

- ✅ O(∣T∣^2/3)
  - *An informal argument for this is as follows: suppose we collect n random samples. The number of triples among the n samples is n choose 3 which is O(n^3). For a particular triple x,y,z to be a 3-way collision we need H(x)=H(y) and H(x)=H(z). Since each one of these two events happens with probability 1/∣T∣ (assuming H behaves like a random function) the probability that a particular triple is a 3-way collision is O(1/∣T∣^2). Using the union bound, the probability that some triple is a 3-way collision is O(n^3/∣T∣^2) and since we want this probability to be close to 1, the bound on n follows.*
- ❌ O(∣T∣^1/2)
- ❌ O(∣T∣)
- ❌ O(∣T∣^1/3)
