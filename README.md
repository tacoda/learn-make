# Make

https://makefiletutorial.com/

## Syntax

A Makefile consists of a set of rules. A rule generally looks like this:

```
targets : prerequisites
  command
```

- The targets are file names, seperated by spaces. Typically, there is only one per rule.
- The commands are a series of steps typically used to make the target(s). These need to start with a tab character, not spaces.
- The prerequisites are also file names, seperated by spaces. These files need to exist before the commands for the target are run.

Valid wildcards are *, ?, [...]