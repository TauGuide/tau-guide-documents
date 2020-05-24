---
title: TML Bot Tutorial
description: An easy-to-use guide to interact with the TML bot
disableTableOfContents: false
---

# TML Bot Tutorial

INTRODUCTION

---

The Tau meta language (TML) bot (mr_tau) can be seen as the first go-to application to experience TML in its current form.

This tutorial shall serve anyone interested in getting first hand TML experience as an easy-to-use guide to interact with the TML bot. This is thought to be a living document being continuously updated as TML, mr_tau and our knowledge around them also is continuously evolving.

**TABLE OF CONTENTS**

---

## 1. Finding the TML bot: mr_tau

To communicate with mr_tau (which is the name of the bot), you first need to know where to find it. There are two places you can go to, to find and interact with the TML bot:

- 1. **Telegram:** You can join the [IDNI Dev Chat](https://t.me/joinchat/ElCYP1TPyRalxhCgi_5HxA). This chat has a bridge to the IRC channel where the bot resides. So you can directly communicate with him from here by writing:

```
*mr_tau: .help*
```

- 2. **IRC:** To communicate with mr_tau over IRC, you can download the [IRC client](http://mirc.com/) or access it via the [web browser](https://webchat.freenode.net/). Choose a nickname and connect to the freenode IRC by clicking “start”. Once connected, you can privately interact with mr_tau by writing:

```
*/query mr_tau .help*
```

This starts a direct conversation with mr_tau asking him for help. From here on,

you can play around with him.

## 2. Talking to mr_tau

As mr_tau prefers to communicate in TML, it is recommended to have a basic understanding of how TML works. You can find an introduction into TML [here](https://github.com/IDNI/TML/blob/master/README.md).

### ▪ 2.1 Commands

To speak out commands to mr_tau, you have to put a dot (.) in front of the command. If

you don’t put a dot in front of your text, mr_tau understands it as TML.

### ▪ 2.1.1 .Help

Command '.help.' shows a basic usage of the bot.

```
.help.
```

This is usually the first command to interact with mr_tau.

mr_tau then will provide you with information about how you can communicate

with him:

*# Each user can create slots and switch between them. Each slot has its own pair of a data database and a program database.*

*# Data database contains only facts which are updated by executing TML code.*

*# Program database contains rules. Use '+RULE' or '-RULE' to add/remove rule to/from a program database.*

*# Use ':SLOT' to switch to another slot. Initial slot is called 'default'.*

*# REPL commands are prefixed by a comma '.'. Use command '.list.' to get list of commands. Use '.help(COMMAND).' to get help for a command.*

### ▪ 2.1.2 .List

This command serves to obtain a complete list of commands and input prefixes

available to communicate with mr_tau.It will answer:

*# Commands: help, list, killall, clear, add, del, db, rules, try, run, slot, list_slots, delete_slot, select, unselect, enable, disable, load, intersect, version. Use '.help(COMMAND).' to get help for the COMMAND.*

*# Input prefixes: . (REPL), + and - (add/del rule), : (selecting slot), / (deleting* # Input prefixes: . (REPL), + and - (add/del rule), : (selecting slot), / (deleting *get help for the PREFIX.* 

*You can also write mr_tau:*

```
*.list(relation REL SLOT).* 
```

 to *display relation REL from slot SLOT. Current slot is used if SLOT omitted.*

### ▪ 2.1.3 .Killall

This command is used to instantly kill all running TML processes. mr_tau will

answer:

*# killing all TML processes*

### ▪ 2.1.4 .Clear

Entering this command will clear both your data and program database. mr_tau:

*# Db cleared*

If you wish to only clear your data database use '.clear(db)' 

```
.clear(db)
```

and if you only wish to clear your program database use '.clear(rules)'.

```
.clear(rules)
```

### ▪ 2.1.5 .Add

Command '.add(rule RULE).' adds new rule 

```
.add(rule RULE).
```

or use '+RULE.' as a shortcut.

```
+RULE.
```

For an explanation of what a rule is, please refer to section [2.1.8 .Rules](https://www.notion.so/TML-Bot-Tutorial-24bbe9a0da404660a4886f62c63d45b7#71f2653188464eb1bce34998d61c679e).

### ▪ 2.1.6 .Del

Command '.del(rule RULE).' deletes the RULE 

```
.del(rule RULE).
```

or use '-RULE.' as a shortcut.

```
-RULE
```

### ▪ 2.1.7 .Db

Command '.db.' or “.db(SLOT).” displays facts contained in the data database of

the SLOT (current slot is listed if omitted). 

```
.db.
```

```
.db(SLOT).
```

If your database is empty, mr_tau will answer:

*## Listing database:*

*## Database is empty*

### ▪ 2.1.8 .Rules

A rule is anything containing “:-”. To a large degree, one can interpret “:-” as

“defined as”. 

Example:

*a(mammal ?x) :- a(cat ?x) 

This rule states: “If x is a cat, then x is a mammal”.*

*Command '.rules.' or '.rules(SLOT).' displays the list of rules (program
database) of the SLOT (current slot is listed if omitted).*

### ▪ 2.1.9 .Try

Command '.try.' or '.try(PROGRAM).' runs data and program databases (with

PROGRAM if provided), displays result and does not update database.

### ▪ 2.2 .Run

Command '.run.' or '.run(PROGRAM).' does the same as 'try' but 'run'

updates the data database if try was satisfied and no error happened

### ▪ 2.2.1 .Slot

Command '.slot.' shows current database slot.

A slot can contain both facts and rules.

### ▪ 2.2.2 .List_Slots

Command '.list_slots.' or '.list_slots(USER). shows list of a user's slot.

### ▪ 2.2.3 .Delete_Slot

Command '.delete_slot(SLOT).' deletes the SLOT. Only user's own slots

which aren't currently selected can be deleted. Use '/SLOT' as a shortcut.

### ▪ 2.2.4 .Select

Command '.select(OPTION VALUE)' store a value by option. Only option

'slot' is currently support.

So you can use the “.select” command to switch in between your slots. Alternatively, you could also write “:slot_name” to switch the slot. Example:

*:bigslot*

Lets you switch from your current slot into the slot with the name “bigslot”.

### ▪ 2.2.5 .Unselect

## Command '.unselect(OPTION)' clears the value stored for the option. If

used with a value ('.unselect(OPTION VALUE)') option is cleared only if the

VALUE argument matches the value currently set. Example:

*.unselect (slot bigslot)*

***Mr_tau:***

*## Unselected slot : bigslot*

### ▪ 2.2.6 .Enable

Command '.enable(OPTION)' enables option. Run '.help(options)' to see list

of options.

Running ‘.help(options)’ provides you with all available options to enable/disable:

### ▪ 2.2.6.1 Auto_print

Enable 'auto_print' to automatically print the database after each run.

### ▪ 2.2.6.2 Print_steps

Enable 'print_steps' to print steps.

### ▪ 2.2.6.3 Print_updates

Enable 'auto_updates' to print updates from rules.

### ▪ 2.2.7 .Disable

Command '.disable(OPTION)' disables option. Run '.help(options)' to see list of options.

### ▪ 2.2.8 .Load

Command '.load(SLOT).' to load facts from another SLOT (SLOT can be slot, slot@user or @user). Use '<SLOT' as a shortcut.

### ▪ 2.2.9 .Intersect

Intersecting is a core part of detecting consensus in between slots and users. By intersecting between two slots, mr_tau will check for an overlap of consensus and answer it to you.

Command '.intersect(SLOT).' to result into intersection of current and another SLOT (SLOT can be slot, slot@user or @user). Use '?SLOT' as a shortcut.

Note: When looking to intersect with a slot of another user, you have to add quotation marks like here:

```
*.intersect(“slot@user”)*
```

Intersect-Example:

In this example, we create the slot “i1”, then add “a.b.” facts. Then, we create the slot “r”, load content of slot “i1” and then intersect it with slot “i2”:
**Me:		:i1**
Mr_tau:	# Selected slot : i1
**Me:		a.b.**
Mr_tau:	# elapsed: 0.25 ms
Mr_tau:	# Total elapsed: 28 ms user: 0.00 s system: 0.00 s memory: 4008 Kb
Mr_tau:	# step: 0
Mr_tau:	a().
Mr_tau:	b().
**Me:		:i2**
Mr_tau:	# Selected slot : i2
**Me:		b.c.**
Mr_tau:	# elapsed: 0.14 ms
Mr_tau:	# Total elapsed: 15 ms user: 0.00 s system: 0.00 s memory: 4028 Kb
Mr_tau:	# step: 0
Mr_tau:	b().
Mr_tau:	c().
**Me:		:r**
Mr_tau:	# Selected slot : r
**Me:		<i1**
Mr_tau:	# Loading data: i1
Mr_tau:	# elapsed: 0.44 ms
Mr_tau:	# Total elapsed: 30 ms user: 0.00 s system: 0.00 s memory: 4076 Kb
Mr_tau:	# step: 0
Mr_tau:	a().
Mr_tau:	b().
**Me:		?i2**
Mr_tau:	# Intersecting: i2
Mr_tau:	# step: 0
Mr_tau:	b().

### ▪ 2.3 .Version

Command '.version.' displays version (commit) of TML used by bot.

```
.version.
```

### ▪ 2.3.1 .Help(COMMAND)

Use this command to get explanatory information on any of the available commands. This document already contains the help information for all commands.

## ▪ 2.4 Entering Facts

mr_tau manages a database for each user. You can add facts to your database by entering it in the following format:

‘RELATION NAME’(CONTENT)

Usually, ‘RELATION NAME’ is being replaced with a verb but it can be anything. Imagine you are creating a table with ‘RELATION NAME’ being the table’s name. Inside the table is the relation.

Example:

*a(Peter human).*

✎[Edit this page on GitHub](https://github.com/TauGuide/tau-guide-documents/blob/master/docs/Tutorials/tml-Bot-tutorial.md)