# Your secrets (best before 1/1/2025): a thought experiment on cryptography's expiration


![BrokenCrypto]({{ '/public/img/posts/2019-10-23-crypto-time-machine/lock-image.jpg' | relative_url }})

Cryptography is a field with deep roots in mathematics. Yet, because of its broad applications, its reach extends into even the simplest activities of our daily lives - sharing a cat photo on instagram, sending a whatsapp/signal message to a friend, making a payment with your credit card. Cryptography, and more specifically encryption, protects the confidentiality of our actions in cyberspace - giving us the peace of mind that someone isn't listening in on our private conversations.

In general, these schemes are built on top of what we believe is secure today. However, as history has shown, what we claim impregnable today may not be so tomorrow. Perhaps our confidence in web privacy has been influenced by confirmation bias. Through this article, we will explore a different perspective of how we view cryptography and privacy.

## Why does encryption work today?

The premise of encryption is based on the idea that some mathematical problems are hard to solve. The most popular example of this is integer factorization:

i.e. I know that the product of two numbers 151 * 251 = 37901. However, if I provide just the final number 37901, finding out which two factors would have produced it is generally hard. Of course, with cryptography this is usually a much larger number.

Because cryptography is based on something being hard to calculate, the security of a scheme is usually tied to the computation power available. For example, in the earlier case where we had the number 37901, a computer today would be able to uncover all possible factors within seconds. However, a very large number (i.e. with >2000 digits) would take several hundreds of years with today's computing power [^1].

Therefore, the claim that an encryption scheme X is secure is usually made with these underlying assumptions:
- Mathematics and crypto-analysis research show that problem X is hard to solve
- Experts predict, given the current trend of computational capabilities, that X cannot be solved in the near future


## Crypto gets broken

In general, the conclusions of the cryptographic community are sound. However, like in any other field, there are exceptions. Maintaining a keen eye on them is especially critical in cryptography because security and privacy are at risk. Two most common scenarios where crypto schemes weaken are when there are new developments in mathematics (potentially from overlooked assumptions) or advancements in computational capabilities.

### Improvement in mathematics and crypto-analysis


Because crypto systems are based on the difficulty of particular math problems. It naturally follows that as scientists and mathematicians make progress in solving those math problems, the security of the crypto scheme gets weaker. This happens fairly often, but usually have a limited impact - i.e. only a very small number of users are affected or the security of the scheme becomes 10% less secure. A couple examples of these attacks are the [sweet32 attack of the 3DES encryption scheme](https://sweet32.info/), and the [Logjam attack on Diffie Helmman](https://en.wikipedia.org/wiki/Logjam_(computer_security)

Fortunately, these types of attacks are usually easy technical fixes, usually by making minor tweaks to the crypto system (i.e. key length, prime sampling). However, the difficulty is not from the correction of the crypto scheme, but the adoption of the new scheme. This is due to the internet is made of thousands of systems, of which there are millions of components - each using the crypto scheme. Therefore, making these changes ends up being a major engineering and standards undertaking due to the need for adoption by systems across the board in order to be effective.

Therefore, some time may need to be taken to ensure that all systems are corrected. The result of this engineering complexity usually ends up in systems supporting interoperability with older insecure protocols for a significant amount of time. While older or less accessible systems (i.e. satellites) need to be updated, components will still need to offer backward compatibility with the older less secure crypto schemes.

There are a class of attacks which take advantage of this, called crypto downgrade attacks. Many of us may be familiar with this concept from how we manage our online accounts. We usually log into our online accounts with a username and password (at least). However, when we lose our password, we fall back to a more insecure way of proving our identity - i.e. a secret question or a password reset email link. These crypto downgrade attacks do something similar, by falsely advertising that a system does not support newer more secure crypto configurations, they force the use of insecure communication protocols. Some examples of this are the recent [POODLE](https://en.wikipedia.org/wiki/POODLE) and [DROWN](https://en.wikipedia.org/wiki/DROWN) attacks.

### Increase in computational capabilities

As computation plays a significant role in the security of cryptography, the improvement of computations is linked to the security of the schemes. A very simple example of this is the increase in computational accessibility. One example of this would be the use of Graphical Processing Units (GPUs) in the cracking of passwords that started to pick up in the late 90s. However, these types of computational advancements are mostly identified well before security becomes an issue. Corrections are usually done in the form
of increasing key length or entropy - i.e. password length changes to require more than 8 characters.

However, one aspect of computational capabilities that can lead a major breakdown of a crypto system also exists. These are from the shift in computation paradigm. An example of this dates back to World War II, where the enigma machine was used to perform encryption of german secrets. Back then the "computers" of the day were humans, and the ability to crack enigma was based on the idea that it would be impractical for a human to crack the code by hand. The
[Bombe](https://en.wikipedia.org/wiki/Bombe) was developed, which is an early prototype for what we know today as classical computers (the one you're using to view or print this article). The shift in what computations were possible changed dramatically and computations that were hard to do became much easier.

In fact, this is VERY relevant in the world we live in today. With the discovery and advancement of quantum computing, certain computations which used to be hard will no longer are anymore. This impacts the encryption that we are performing today. In fact, RSA, which is what we use today in many of our web browsers for public key cryptography would be cracked easily with quantum computing.
Very much like [Ada Lovelace](https://en.wikipedia.org/wiki/Ada_Lovelace) in the 19th century who developed algorithms for classical computers before they existed, there are scientists today like [Peter Shor](https://en.wikipedia.org/wiki/Peter_Shor) who develop algorithms for quantum computers. [Shor's algorithm](https://en.wikipedia.org/wiki/Shor%27s_algorithm) performs integer factorization on a quantum computer efficiently. This would break most encryption schemes based on integer factorization, like the aforementioned RSA crypto scheme.

This would mean that most of what we assume is encrypted and confidential today, will be decryptable by almost anyone in due time... when quantum computers mature.

## What does this mean for us?

So what does this mean? Should we assume that all our data that we send over the internet is going to be accessed by someone? Theoratically, if someone or organization were to start sniffing all the data on the interenet, eventually, your data would be retrievable by them. However the question here shouldn't be "if my data will be exposed", but it should be "when my data will be exposed?". This is similar to the idea of [Timelock Puzzles](https://people.csail.mit.edu/rivest/pubs/RSW96.pdf), where information is not decryptable until a certain time has passed. In this case, the amount of time is based on how long it takes that the crypto system that we use gets broken.

If my bank PIN would to be cracked 200 years later, would that matter if my bank account (or the bank) doesn't exist anymore? This can lead to a philosophical discussion, but the bottom line would be whether you consider the information that you are encrypting over the internet today still confidential a hunderd or more years from now - maybe if one were famous or had a legacy to uphold. An example recently is this article showing that Ken Thompson's unix password on an old UNIX system being cracked. It is not really a big deal since the system doesn't exist anymore - but we did find out that he likes chess (maybe)!

Ending on a lighter note, the general guarantees of today's crypto schemes are pretty good, and there are already schemes available which are quantum-safe. So if one uses a good crypto algorithm with best practices configurations, there is little to worry about for the future. For the times where information should be sealed away for eternity, like certain memes of today, there are encryption schemes that are [Information-theoratically secure](https://en.wikipedia.org/wiki/Information-theoretic_security), this means based on information theory they will never be recoverable. However, these schemes are not practically for general, because they bring with them a lot of inconvenience, especially in terms of key exchange.

But for now... maybe it's okay if 50 generations later, our descendents finally get their hands on that well kept trade secret KFC recipe to enjoy on Mars :).

[^1] https://www.digicert.com/TimeTravel/math.htm
