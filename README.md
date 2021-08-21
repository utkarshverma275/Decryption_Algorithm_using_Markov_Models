# Decryption_Algorithm_using_Markov_Models

## Aim
Our aim here is to understand the core logic of handling a Machine Translation problem in the domain of  Natural Language Processing.
There are many libraries for NLP problems : beginner , intermediate and advanced. Our motive is to understand why we need these libraries.
We do this by build basic versions of advanced libraries like Gensim, SpaCy, and build our own methods that do lemmatization, N-grams, Markov Models etc.
This excersize is purely to develop intuition on how to approach NLP problems in the real world. 

##Ciphers
Ciphers, also called encryption algorithms, are systems for encrypting and decrypting data. A cipher converts the original message, called plaintext, into ciphertext using a key to determine how it is done.

Ciphers are generally categorized according to how they work and by how their key is used for encryption and decryption. Block ciphers accumulate symbols in a message of a fixed size (the block), and stream ciphers work on a continuous stream of symbols. 
When a cipher uses the same key for encryption and decryption, they are known as symmetric key algorithms or ciphers. Asymmetric key algorithms or ciphers use a different key for encryption/decryption.

Here we do something very simple. Substitution cipher. Any letter in the plaintext is substituted by another "predefined" letter.

## Problem
We are going to build an NLP model that works as a decryption algorithm for a substitution cipher.

PlainText Expression : "GOD IS EVERYWHERE"

#### Cipher Algorithm

G => A; O => B; D => C ; 

I => D ; S => E ; 

E => F ; V => G ; R => H ; Y => I ; W => J ; H => K 

We can say the cipher is a dictionary that has a 1:1 mapping for each alphabet and its key. For example G has a unique key A. G is written as A in the cipher

When we apply this cipher to the expression, we obtain :

"ABC DE FGFHIJKFHE"


#### Decryption Algorithm
The decryption algorithm will take "ABC DE FGFHIJKFHE" and give us back "GOD IS EVERYWHERE"  


## How to solve the Problem 

Lets understand the challenge in building a decryption algorithm.
-   There are 26! (factorial) possible combinations for the decryption algorithm. Only one of this is true. Lets call the decryption algorithm as F.
-   Even if we build 26! combinations of F, each F when applied to the expression will yield 26! results. A human will have to inspect the results and figure out which is an understandable message.

To address challenge #1 we need to have an apporach that minimizes the number of attempts to guess F

To address challenge #2 we need to build a model that can differentiate between English and Gibberish.
For example if the result is "ZYX MN STSGJFSTN" our model should say this is Gibberish , i.e. the decrytion algorithm we have guessed is not good. 

Challenge #2 can be solved using the following approach 
We want to build a probalistic model that assigns high probability to real words and sentences and assigns a lower probability to anything that's not real english or gibberish.

Let call this model H

H('ASD OP DKDKDKGSK') = small number

H('I LIKE TO SWIM') = large number
