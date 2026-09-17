
# Overview

- **name** are uppercase. **values** are string
- **prepend, append or define**

- **GLOBAL SCOPE:** ==variables defined in CONFIGURATION FILES== <- files ending with .conf
- **LOCAL SCOPE**: ==defined in Recipes== <- files ending in .bb, .bbappend, ..bbclass
- [[03-Recipes]] can also access the global scope

# Basic assignment


```
VAR = "this"
VAR = "that"

result: VAR = "that"
```

- newlines need to be escaped
- Variable assignments can contain expansion of other variables:
```
COLOUR = "blue"
SKY = "the sky is ${COLOUR}"
```

## Immediate expansion
- = happens when the variable is used
- := for immediate expansion
```
COLOUR = "blue"
SKY = "the sky is ${COLOUR}"
COLOUR = "grey"
PHRASE = "Look, ${SKY}"
```
===result: "Look, the sky is grey"

```
COLOUR = "blue"
SKY := "the sky is ${COLOUR}"
COLOUR = "grey"
PHRASE = "Look, ${SKY}"
```
===result: "Look, the sky is blue"

=> **normal expansion in most case. Only use := when needed**

## Appending and Prepending
- += append (with space)
- .= append (without space)
- =+ prepend (with space)
- =. prepend (without space)

## Default and weak default values
- ?= Weak assignment: assigns a value **only if the variable has not been assigned** when the statement is parsed.
- ??= Even Weaker Assignment: "laziest". It sets a default value **only if the variable has not been assigned at all - not even with a **  ?= operator


