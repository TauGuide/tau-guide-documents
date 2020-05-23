---
title: Understanding TML
description: A deep dive into the tech behind Tau's Meta-Language (TML).
disableTableOfContents: false
---

# Understanding TML: Prolog -> Datalog -> Tau

by Dana Edwards

Source: 

[Understanding TML: Prolog -> Datalog -> Tau - Steemit](https://steemit.com/tauchain/@dana-edwards/understanding-tml-prolog-datalog-tau)

This post will explore some concepts behind logic programming. In Ohad's examples on Github he has as inputs his logic programs. For the most part all logic programs work the same way and the initial syntax of Tau is essentially almost an exact copy of Prolog or Datalog. So let's learn a bit of Prolog?

Step 1: Install [SWI Prolog](http://www.swi-prolog.org/).

Step 2: Watch this [video](https://www.youtube.com/watch?v=gJOZZvYijqk).:

[https://www.youtube.com/watch?v=gJOZZvYijqk](https://www.youtube.com/watch?v=gJOZZvYijqk)

The basic concepts to learn to know Prolog/Datalog/Tau:

- We have facts, rules, and queries (clauses).
- We have variables (X, Y, Z). Variables must be in capital letters.
- We have recursion which is a function that can keep calling itself until the goal is complete.
- We have unification.

Facts are statements such as:

Socrates is mortal.Mortals are human.

In Prolog:

human(socrates).mortal(human).

The arity is the number of arguments passed.

So this example from Ohad:

uncle(jim, joe)

Has an arity of 2. Why? Because there are two arguments being passed (jim, joe).

When we write our facts we are creating the knowledge base. In Tau these facts would be input via our discussions. So the fact uncle(jim,joe) in plain English is saying Jim and Joe are uncles. The predicate here would be uncle.

Rules are important as well. A rule can be thought of as an extension of a fact but with conditions to be satisfied in order for it to be true. So for example we have the implication symbol " :- " which we use when working with rules.

So for example:

human(X) :- man(X).human(Y) :- woman(Y).

This says in plain English: All man are human. All woman are human. Put another way, man or woman implies being human.

If a predicate contains a goal which refers to itself then we have recursion.

Here is the full logic program I wrote for Socrates is human:

%factsman(socrates).woman(eve).

%%ruleshuman(X) :- man(X).human(Y) :- woman(Y).

To query you simply can ask "is Socrates human?" by typing: human(socrates).The answer can be either true or false. Unification takes place, as socrates unifies with X. Simply type: " man(X). " or " woman(y). " as the queries to confirm unification.

Because we know from the facts that Socrates is a man, and from the rules if human is x then man is x "if it's a man then it's a human", then we know Socrates has to be a human.

We can also ask if eve is human by asking via the same query: human(eve). This should immediately illustrate the potential power of logic programming and also put into context exactly what Tau does with it's binary decision diagram portion of the code. We can see that this kind of logic is:

```
If p then q;
    p;

```

∴ q.

If Socrates is a man then Socrates is human.Socrates is a man.Therefore Socrates is human.

We can do [cryptography](https://www.metalevel.at/prolog/cryptography) by using library(crypto).

Remember, it's subject, **predicate**, object.

To do basic symmetric cryptography you must:

1. Provide the algorithm you want to use.
2. The key used for the encryption.
3. The initiation vector.

It's much much easier than C++. Let's take a look?

use_module(library(crypto)).

This tells Prolog to use the crypto module.

crypto_data_hash('Socrates is human!', Hash, [algorithm(sha256)]).

This says that the string "Socrates is human!" is crypto_data_hash using sha256.

Before you can do any encryption you typically have to turn a string into a hash value. Our predicate is the part of subject, predicate, object, which tells us what the data does. So the string gets hashed by algorithm sha256.

crypto_n_random_bytes(32, Ks),crypto_n_random_bytes(32, IV),crypto_data_encrypt(test, 'aes-256-cbc', Ks, IV, CipherText, []).

The structure of the data here are in the form of "bytes". As we can see, we are saying here that the random number generator crypto_n_random_bytes is a 32bit key. The how to guide for using this predicate is:

[crypto_data_encrypt(+PlainText, +Algorithm, +Key, +IV, -CipherText, +Options)](http://eu.swi-prolog.org/pldoc/doc_for?object=crypto_data_encrypt/6)

## **References**

1. [https://swish.swi-prolog.org/](https://swish.swi-prolog.org/) 

[SWISH -- SWI-Prolog for SHaring](https://swish.swi-prolog.org/)

1. [https://github.com/IDNI/tau](https://github.com/IDNI/tau) 

[IDNI/TML](https://github.com/IDNI/tau)