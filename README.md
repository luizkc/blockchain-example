# Key Terms:

- **Block**: a block is an individual transaction or piece of data that is being stored within the blockchain.
- **Blockchain**: a continuously growing list (*chain*) of records (*block*) called blocks, linked chronologically and secured with cryptography.
- **Blockchain Network**: blockchain network and blockchain are terms used interchangeably. They represent the entire blockchain from the structure itself to the network that it is a part of.
- **Decentralization**: the concept in which participants work together to validate transactions without relying on a central authority.
- **Participant**: a client that owns a copy of the blockchain and verifies transactions across the network.
- **Timestamp**: the time the block is created determines the location of it on the blockchain. every block contains a timestamp.
- **Transaction Data**: the information to be securely stored in the block
- **Hash**: a calculated string of letters and numbers produced from a specific input.
- **Previous Hash**: each block has a reference to the block prior to it. This is what makes the blockchain unique because this link will be broken if a block is tampered with.
- **Hash Function**: a function that takes in an input of a random size, performs hashing on the input, and generates a seemingly random output of a fixed size, also known as a hash.
- **Deterministic**: the same input will always produce the same output, but that output cannot produce the original input.
- **Genesis Block**: the first block on the blockchain and it is typically hard-coded into the blockchain structure. Being the first block on the blockchain, it does not have a link to a previous hash.
- **Transactions**: An exchange of value among participants on the blockchain network.
- **Participants**: Individuals accessing the blockchain network through computers to exchange value.
- **Unconfirmed**: Blocks and transactions that are yet to be verified.
- **Consensus**: The process of agreeing to the transactions on the blockchain network.
- **Recalculating Hashes**: Replacing the incorrect hash with a “correct” one to validate the chain.
- **Proof-of-Work**k: A security feature in blockchain to prevent attackers from easily taking over the blockchain.
- **Trustless**: A feature of blockchain that states how the system doesn’t rely on any participant to verify transactions.
- **Miners**: Special participants who calculate the Proof-of-Work to mine new blocks.
- **Nonce**: A number to be guessed by miners which when combined with the block produces an acceptable hash.
- **Longest Chain**: The most trusted chain with the largest amount of computational work done in calculating the Proof-of-Work.
- - **Immutable**: Something whose records can’t be changed.

# Blocks

- blocks can hold different types of data depending on what the blockchain is for.
- a block will always contain a timestamp or data regarding the time the block was created.
- each block has a unique hash.
- each block contains a previous has, or a reference to the previous block on the chain

## Block Properties

- **Timestamp**: The time the block is created determines the location of it on the blockchain.
- **Data**: The information to be securely stored in the block.
Hash: A unique code produced by combining all the contents within the block itself — also known as a digital fingerprint.
- **Previous Hash**: Each block has a reference to the block prior to its hash. This is what makes the blockchain unique because this link will be broken if a block is tampered with.
- **Immutable**: Something whose records can’t be changed.

# Hashing/Security

- a unique code produced by combining all the contents within the block itself, also known as a digital fingerprint..
- an application of cryptography.
- a way to generate a seemingly random, but calculated, string of letters and numbers from any input using what is called a hash function.
- hash functions in a blockchain are deterministic, meaning the same input will also generate the same output (or hash code).
- a block's hash changes when a participants attempts to modify/tamper the data.
  - this breaks the chain and render it invalid

## What happens when a hash changes?

 If a participant decides to tamper with a block by modifying the transactions, the block’s unique hash gets changed. However, the following block does not update to reflect this change — it still points to the previous block’s hash. Thus, there is a mismatch between hashes and the link between blocks is broken. This results in an invalid copy of the blockchain.

 In this way, the records in the blockchain cannot be altered. In other words, the records are said to be **immutable**.

 ## Excerpt: the theory of "hacking" a blockchain

What if an attacker tampers with a block and then somehow covers their tracks by recalculating the hash of each subsequent block to make the blockchain valid once again? Let’s explore this concept through an example.

Let’s say we have three blocks: A, B, and C with hashes X123, Y456, and Z789 that represent the state of each block. If an attacker tampers with Block A, its contents get changed, so its hash gets changed — let’s say the hash is changed from X123 to 123X. Block B no longer points to Block A because the previous hash X123 no longer matches with the new hash 123X. The only way for the attacker to make the chain valid is by fixing this mismatch. For Block B to point to Block A, its previous hash needs to be changed from X123 to 123X.

However, this also counts as tampering with Block B’s data. Thus, its hash also gets changed. If the attacker repeats this process for all subsequent blocks, they will have succeeded in creating a valid copy of the blockchain!


This brings us to the next layer of security added to a blockchain to make them invulnerable to this.

# Proof of Work

A security feature in blockchain to prevent attackers from easily taking over the blockchain.

## Why?

Since participants on the blockchain network are anonymous users on their computers, we can’t trust them to verify transactions honestly.

Proof-of-Work does nothing more than introduce an additional security constraint to verify transactions. This constraint takes the form of a computationally difficult math problem, which means to say that it takes a lot of time even for the computer to solve the problem.

## The process

When a new block is attempted to be verified, *miners* must play a guessing game. This game involves using giving a hash function a random number paired with the block's data as input. If the output of the function is a hash equal to the *nonce*, the block is then verified.

The first miner to guess the nonce broadcasts their *proof-of-work* (the input given to the hash function that generated the nonce) with the unconfirmed block and the correct nonce. 

The rest of the network can then verify the calculation. If consensus is reached and the majority of the participants agree, the proof-of-work is complete and block is confirmed.

The network then moves on to confirm the following blocks.

# The longest chain is always the correct one

The blockchain participants always consider the longest chain to be the correct one. If someone is able to create the longest chain of blocks (even if the blocks are fake), the network is forced to accept the new chain.

The reason for this is simple — the blockchain network assumes that the longest chain has the most amount of computational work done in finding the Proof-of-Work for each block. Therefore, it is reasonable for the network to think that the longest chain contains the most proven record of transactions.

If a dishonest participant decides to tamper with a block, they would have to solve the Proof-of-Work for each subsequent block in order to introduce the tampered block into the network. **This is computationally infeasible and almost impossible!**

Furthermore, while the participant is busy finding the Proof-of-Work for each block, newer blocks are being added to the blockchain at a faster rate. The participant soon finds out that they are playing a losing battle against the entire network.

## Takeaway

A block gets increasingly more tamper-proof as newer blocks are added next to it. Proof-of-Work makes it hard to get through the entire blockchain and allow someone to introduce a fake transaction.

# Verification

1. transaction is placed in the *mempool*.
2. latest transactions in the *mempool* are broadcasted to all participants.
3. each participant collects these transactions into a new block. Each block can hold a limited number of transactions.
4. the remaining transactions in the *mempool* must wait for their turn once a block is full.
5. once a block is full, ait is said to be *unconfirmed* and the transactions inside of it are said to be invalid.
6. assuming participants know how to verify transactions and are honest: once 51% of participants agree that a transaction is verified, meaning they have reached a **consensus**, the block is now said to be *confirmed*.
