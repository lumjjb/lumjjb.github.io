# Our secrets today, no longer tomorrow: a thought experiment in cryptography


![BrokenCrypto]({{ '/public/img/posts/2019-10-23-crypto-time-machine/lock-image.jpg' | relative_url }})

Cryptography is a topic deeply rooted in mathematics, but because of its broad applications, it has an impact on each and every one of us today - be it sharing a cat photo on instagram, sending a private whatsapp/signal message to a friend, to the process of making a payment using your credit card. Cryptography, and more specifically encryption, helps provide confidentiality of our actions in the cyberspace - giving us peace of mind that someone isn't listening to our private
conversations.

In general, these schemes are built on top of what we believe are secure today. However, as history has shown us, what we deem secure today, may not be tomorrow. Perhaps our confidence in the privacy of our activities on the internet are influenced by confirmation bias. Through this article, we will explore a different perspective of how we view cryptography and privacy.

## Why does encryption work today?

The premise of how encryption works is based on some mathematical problems being hard to solve. The most popular example of this is integer factorization:

i.e. I know that the product of two numbers 151 * 251 = 37901. However, if I just provide the number 37901, finding out that the two factors of the number is generally hard. Of course, with cryptography, it usually is a much larger big number.

Because cryptography is based on something being hard to calculate, the security of a scheme is usually tied to computation power available. For example, in the case earlier where we had the number, 37901, a computer today would be able to try all possible factors of the number within seconds. However, a very large number (i.e. with 2000+ digits) would take multiple 100s of years by today's computer power [^1].

Therefore, The ability to say that an encryption scheme X is secure is usually on the basis of:
- Mathematics and crypto-analysis resaerch shows that problem X is hard to solve
- Experts predict that given current trend of computational capabilities of the near future, X cannot be solved

## Crypto gets broken

In general, the conclusions of the cryptographic community are sound, but like any other field, there are overlooked scenarios or external factors that influence the strength of an encryption scheme. This is especially critical in cryptography because security and privacy is affected. Two most common scenarios where crypto schemes weaken are when there are new developements in mathematics/overlooked mathematical assumptions or improvements in computational capabilities.

### Improvement in mathematics and crypto-analysis

The first situation where crypto schemes degrade in security is from the progress of mathematics and/or crypto-analysis. These usually come in the form of new types of attacks on crypto schemes. These attacks usually take the form like the following:
- If a key generated happens to meet certain properties, it is easily breakable.
- There is a new attack which makes computation of breaking this scheme feasible, a larger key needs to be used

A couple examples of these attacks are the [sweet32 attack of the 3DES encryption scheme](https://sweet32.info/), and the [Logjam attack on Diffie Helmman](https://en.wikipedia.org/wiki/Logjam_(computer_security)). These types of attacks usually affects the security of the crypto protocol leading to a need to change parts of the protocol, or tweak parameters used in the protocol (i.e. key length, prime sampling).

We note that these attacks are generally able to be resolved by making tweaks to the configuration of the crypto scheme. However, this is a major engineering and standards undertaking as it involves multiple systems interacting with each other. Therefore, some time may need to be taken to ensure that all systems are corrected. The result of this engineering complexity usually ends up in systems supporting interoperabibility with older insecure protocols for a significant amount of time. This need for backward compatibility also becomes
susceptible to a recent class of downgrade attacks - basically a malicious system claims that it does not support a new standard of encryption, and asks the user to use the insecure version instead. Such examples are the recent [POODLE](https://en.wikipedia.org/wiki/POODLE) and [DROWN](https://en.wikipedia.org/wiki/DROWN) attacks.

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
