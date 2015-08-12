---
layout: post
title: "Side channel crypto attacks"
quote: "RSA Key Extraction via Low-Bandwidth Acoustic Cryptanalysis."
image: false
video: false
comments: true
---

I had miss this [great article](http://www.cs.tau.ac.il/~tromer/acoustic/) from Daniel Genkin, Adi Shamir and Eran Tromer. 

- [Video presentation](https://www.youtube.com/watch?v=DU-HruI7Q30)
- [Full paper](http://www.cs.tau.ac.il/%7Etromer/papers/acoustic-20131218.pdf)

They explain how different RSA keys induce different sound patterns, but due to the very low bandwidth of the acoustic side channel it was not clear to them how to extract individual key bits.

They continue describing a new acoustic cryptanalysis key extraction attack, applicable to GnuPG's current implementation of RSA. 
The attack can extract full 4096-bit RSA decryption keys from laptop computers (of various models), within an hour, using the sound generated by the computer during the decryption of some chosen ciphertexts.
They present experimental results demonstrating that such attacks can be carried out, using either a plain mobile phone placed next to the computer, or a more sensitive microphone placed 4 meters away.

Beyond acoustics, they also demonstrate how a similar low-bandwidth attack can be performed by measuring the electric potential of a computer chassis. A suitably-equipped attacker need merely touch the target computer with his bare hand, or get the required leakage information from the ground wires at the remote end of VGA, USB or Ethernet cables.

Now imagine that you carry the attack using the victim mobile phone by activating the microphone remotely...

Till next time, then!