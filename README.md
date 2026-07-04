# Dan's Reverse Polish Language

[![Greenkeeper badge](https://badges.greenkeeper.io/emberdart/drpl.svg)](https://greenkeeper.io/)

## Running

`npm run example` will run an example

`npm test` will run tests

`./drpl FILE` or `npm run drpl FILE` will interpret `FILE`.

## Aims

Aims to have as few commands as possible with macros to extend.
Stack based.

Considerations: A read only stack or a preinitialised stack. Maybe needs return codes.

## Commands

### stdlib

```
w write: Pops fd, string. Pushes nothing.
c copy: Pops any, Pushes two any.
+ add: Pops two numbers, pushes one.
- sub: Pops two numbers, pushes one.
* mul: Pops two numbers, pushes one.
/ div: Pops two numbers, pushes one (dies horribly if #2 is 0).
s swap: Pops two any, pushes in reverse order.
```

Accepts quotes " \` or '

### colours

```
col: pops type, colour, pushes string.
    types:
        fg: foreground
        bg: background
        set: setting
    colours:
        black
        red
        green
        yellow
        blue
        magenta
        cyan
        white
    settings:
        rst: reset
        brt: bright
        dim: dim
        usc: underscore
        bln: blink
        rev: reverse
        hdn: hidden
```

Example:
```
"This should be red." red fg col + 1 w
"This should not." rst set col + 1 w
```

## Future

### Commands
```
r read: Pops fd, string. Pushes nothing.
b blocking-read: Pops fd, string. Pushes nothing.
f func: May define a function or macro somehow later.
j jump: may not be needed since we want it more functional
l loop: may or may not be a macro depending on
```

If labels and gotos are necessary, probably it'll be:
```
labelname:
0 @labelname jne (jump if not equal)
```

### Example

Loops?

`100 c 1 w l: BOBOTW 1 w c 1 w BOB 1 w TODAPIA 1 w - c 1 w 1 @l jne`

### Macros

```
p print: 1 w
i input: 0 b
l loop: something like je e 0 - e; which would require asm's je
but we might not do jumping hmm...
```

### Syntax highlighting extensions

??? Researching.

## Disclaimer

I may have just reinvented Forth. But it's fun.
