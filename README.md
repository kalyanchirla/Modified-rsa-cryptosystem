# Modified RSA Cryptosystem Based on Offline Storage

## Description

The RSA cryptosystem is one of the most commonly used public key algorithms for secure message transmission. In the RSA algorithm, two distinct keys are used to encrypt the message and decrypt the encrypted message. The *public key* is used to encrypt the data based on two prime numbers along with a number *N*. The public key can be passed to anyone along the network. To decrypt the message encrypted with public key, a *private key* is required. The public key and private key are generated using the two prime numbers which also need to kept secret. However, there is less security and time of computation is lengthy in RSA Algorithm.

This project is an implementation of a Modified RSA algorithm described in [IEEEXplore](https://ieeexplore.ieee.org/document/6724176) which use a third prime number in order to make a modulus n which is not easily decomposible by intruders. The key parameters of algorithm are stored locally before the computation on input message to increase the speed of computation.

## Modified RSA Algorithm

Consider these assumptions for the algorithm:
- P,Q and R are prime numbers
- n is common modulus
- e is public key
- M is message

The algorithm is as follows:
- Select the random values P,Q and R which are distinct
- Calculate $N=P*Q*R$
- Calculate $\phi(n) = (P-1)*(Q-1)*(R-1)$ 
- Calculate $e$ such that $gcd(e, \phi(n))=1$ and $1<e<\phi(n)$
- Encrypt the message $M$ where $M<n$ and encrypt with public key $e$ such that C=M<sup>e</sup>mod n
- Calculate private key d = e<sup>-1</sup> (mod $\phi(n)$)
- Decrypt the message M such that M = C<sup>d</sup>mod n

***Note:*** Calculating M<sup>e</sup> and C<sup>d</sup> are the most time consuming steps of this algorithm as we are dealing with very large prime numbers. I have used **Binary Exponentiation** to solve this problem of calculating the powers by reducing the time complexity from $O(e)$ and $O(d)$ to $O(log(e))$ and $O(log(d))$ 

## Software Requirements
- [Python3](https://www.python.org/downloads/)
- [Pandas](https://pandas.pydata.org/docs/getting_started/install.html)

## Getting Started

In this project, the input is given in a text file. Let us suppose, we have save a message that we want to encrypt into a text file with the name `data.txt`. (*The name of input text file can be anything of your choice*).

Run: `$ python main.py data.txt`

This runs the modified rsa algorithm taking the data from input text files provided and outputs the encrypted text into `encrypted.txt` in the same directory. The decryption phase is also implemented in this project which takes the encrypted text as input as ouputs the decrypted text into `decrypted.txt`. You can use the decrypted output for verification of the algorithm.

## References
- [Modified RSA Cryptosystem Based on Offline Storage and Prime Number](https://ieeexplore.ieee.org/document/6724176)

## Authors
* **Kalyan Chirla**