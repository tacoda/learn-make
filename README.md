# Make

https://makefiletutorial.com/

## Syntax

A Makefile consists of a set of rules. A _rule_ generally looks like this:

```
targets : prerequisites
  command
  command
  command
```

- The _targets_ are file names, seperated by spaces. Typically, there is only one per rule.
- The _commands_ are a series of steps typically used to make the target(s). These need to start with a tab character, not spaces.
- The _prerequisites_ are also file names, seperated by spaces. These files need to exist before the commands for the target are run.

The main use of Make is to list out a set of directions to compile some c or c++ files, although it can solve other similar problems. The user gives Make some goal, say “generate the file hello”. The Makefile specifies how to make this file.
[Example](01_overview/Makefile)

This makefile has a single target, called some_file. The default target is the first target, so in this case some_file will run.

This file will make some_file the first time, and the second time notice it’s already made, resulting in make: 'some_file' is up to date.

Alternative syntax: same line

The backslash (“\”) character gives us the ability to use multiple lines when the commands are too long

Here, the target some_file “depends” on other_file. When we run make, the default target (some_file, since it’s first) will get called. It will first look at its list of dependencies, and if any of them are older, it will first run the targets for those dependencies, and then run itself. The second time this is run, neither target will run because both targets exist.

This will always make both targets, because some_file depends on other_file, which is never created.

“clean” is often used as a target that removes the output of other targets.

Adding .PHONY to a target will prevent make from confusing the phony target with a file name. In this example, if the file “clean” is created, make clean will still be run. .PHONY is great to use, but I’ll skip it in the rest of the examples for simplicity.

Variables can only be strings.

Implicit commands: Probably one of the most confusing parts about Make is the hidden coupling between Make and GCC.

We can use wildcards in the target, prerequisites, or commands.
Valid wildcards are `*, ?, [...]`

## The Wildcard Function

[Makefile](./06_wildcard_function/Makefile)

We CANNOT use wildcards in other places, like variable declarations or function arguments
Use the wildcard function instead.

{{#inlcude 06_wildcard_function/Makefile}}