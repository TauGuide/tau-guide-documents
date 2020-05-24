---
title: Analysis of TauBot.TML
description: An Analysis of Taubot.tml. The first application to be written in Tau's Meta-Language
disableTableOfContents: true
---

# Analysis of TauBot.TML

by Dana Edwards.

Source:

[Analysis of TauBot.TML - Steemit](https://steemit.com/tauchain/@dana-edwards/analysis-of-taubot-tml)

This is an analysis of TauBot.TML. This is the bot written in TML and is officially the first TML app written. Let's look and see how it works piece by piece?

The program below is broken into parts as all TML or Prolog programs are. We have our clauses which are the FACTs and the RULEs.

For example as a fact:

system(clear db)

This says clear database is part of system. An atom is what is between (), so system(atoms) just as in Prolog. What does an atom even mean? Essentially atoms are like "strings" in C or C++, but in this case atoms break down into numbers at least in Prolog. In TML essentially if we say:

human(socrates).mortal(X) :- human(X).

We know it says Socrates is a mortal. So when we see:

system(clear db)

It's saying that clear db are part of system.

Under system we have output. Which is to say output is a part of or type of system.

system(output0 "# Db cleared"):- clear(db)

Output in this context is similar to write in Prolog. The code above is a rule.

For example:

mortal(X) :-human(X).

This rule in English says for all X, X is mortal if X is human.So if we query: mortal(socrates) it says yes. This is equivalent to asking "Is Socrates a mortal?" and getting the answer "yes". Alternatively you can ask "Who is mortal?" by going with: mortal(X). which should list Socrates and whomever else you added into the database.

The rule says:

system(output0 "# Db cleared") :- clear(db)

Rules are generally broken into head and body.

system(clear db),system(output0 "# Db cleared"):- clear(db).

The rule says if clear(db) then output0 "Db cleared" to the user.

system(db),system(output0 "# Listing database:"),~db:- db.

Now here you see one of the features in TML which does not exist in Prolog. We see the deletion operator ~

Negation and Deletion are unique features of TML. Note TML also supports variables which begin with ?.

So when we see lines like this:

rules(?slot ?rule),~add(rule ?rule),system(output0 "# Added rule: " ?rule),system(rebuild_rule ?rule):- add(rule ?rule), selected(slot ?slot).

~rules(?slot ?rule),~del(rule ?rule),system(output0 "# Removed rule: " ?rule),system(rebuild_rule ?rule):- del(rule ?rule), selected(slot ?slot).

Here we can see that not only do we have rules but we also have variables. These rules describe how to add or delete a rule from the slots. Excuse the terminology here as it confuses me too but a slot is related to how the TML Bot manages record keeping for the database.

So you can now see how to read all the database facts and rules for the TML Bot. To improve this bot we need the ability to read or to take input into the from users system. We can expect that this will be one of the next features coming at some point. There is also a need for useful builtins so that the bot can be made much more sophisticated and maybe even connect to a blockchain.

✎[Edit this page on GitHub](https://github.com/TauGuide/tau-guide-documents/blob/master/docs/Tutorials/analysis-of-taubot-tml.md)