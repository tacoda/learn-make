# Make

https://makefiletutorial.com/

## Syntax

A Makefile consists of a set of rules. A _rule_ generally looks like this:

```make
targets : prerequisites
  command
  command
  command
```

- The _targets_ are file names, seperated by spaces. Typically, there is only one per rule.
- The _commands_ are a series of steps typically used to make the target(s). These need to start with a tab character, not spaces.
- The _prerequisites_ are also file names, seperated by spaces. These files need to exist before the commands for the target are run.

## Make Overview

[Makefile](./01_overview/Makefile)

The main use of Make is to list out a set of directions to compile some c or c++ files, although it can solve other similar problems. The user gives Make some _goal_, say “generate the file hello”. The Makefile specifies how to make this file.

## Running the Examples

```sh
$ make
echo "int main() { return 0; }" > blah.c
cc -c blah.c -o blah.o
cc blah.o -o blah
```

Some examples, like the above, have a target called “clean”. Run it via make clean to delete the files that make generated:

```sh
$ make clean
rm -f blah.o blah.c blah
```

## Simple Examples

[Makefile](./02_simple_examples/iteration_1/Makefile)

This makefile has a single target, called `some_file`. The default target is the first target, so in this case `some_file` will run.

[Makefile](./02_simple_examples/iteration_2/Makefile)

This file will make `some_file` the first time, and the second time notice it’s already made, resulting in `make: 'some_file' is up to date.`

[Makfile](./02_simple_examples/iteration_3/Makefile)

Alternative syntax: same line

[Makefile](./02_simple_examples/iteration_4/Makefile)

The backslash (“\”) character gives us the ability to use multiple lines when the commands are too long

[Makefile](./02_simple_examples/iteration_5/Makefile)

Here, the target `some_file` “depends” on `other_file`. When we run `make`, the default target (`some_file`, since it’s first) will get called. It will first look at its list of _dependencies_, and if any of them are older, it will first run the targets for those dependencies, and then run itself. The second time this is run, neither target will run because both targets exist.

[Makefile](./02_simple_examples/iteration_6/Makefile)

This will always make both targets, because `some_file` depends on `other_file`, which is never created.

[Makefile](./02_simple_examples/iteration_7/Makefile)

`clean` is often used as a target that removes the output of other targets.

[Makefile](./02_simple_examples/iteration_8/Makefile)

Adding `.PHONY` to a target will prevent make from confusing the phony target with a file name. In this example, if the file “clean” is created, make clean will still be run. `.PHONY` is great to use, but I’ll skip it in the rest of the examples for simplicity.

## Variables

[Makefile](./03_variables/Makefile)

Variables can only be strings.

## Implicit Commands

[Makefile](./04_implicit_commands/Makefile)

Probably one of the most confusing parts about Make is the hidden coupling between Make and GCC.

## Using Wildcard Characters

[Makefile](./05_wildcard_chars/Makefile)

We can use wildcards in the target, prerequisites, or commands.
Valid wildcards are `*, ?, [...]`

## The Wildcard Function

[Makefile](./06_wildcard_function/Makefile)

We CANNOT use wildcards in other places, like variable declarations or function arguments
Use the wildcard function instead.
