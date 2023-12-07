# Hacker Typer

Only the most leet hackers can type faster than my bot. Can you beat it?

https://hacker-typer.tuctf.com

## Solution:

1. Just type fast to get the flag.
2. Use selenium or requests to automate

---

# Plenty O Fish in the Sea

You have embarked on a quest to find the One Bit! Your first step is to find the scattered pieces of the treasure map on this here abandoned island!

## Solution:

1. File has repeated lines. Use python to get only unique lines. These lines form the flag
2. The flag is URL encoded. Decoding it gives flag

### Flag: TUCTF{83h!Nd_7h3_W@73rF@11}

---

# Bludgeon the Booty

You have found me treasure chest, but can you crack its code?

---

"This here lock be cursed by the shaman of the swamp to change keys for each attempt"

nc chal.tuctf.com 30002

## Solution:

1. Brute force turning the wheels

---

# Titular Treasure Triangulation

The map led you to this here sandbar. Can you Triangulate the location of the chest?

(((25,189), 307), 54) ((458, 429), 319) (420, 4) ((174, 2), 290) (((323, 42), 8), 113) (((12, 396), 530), 570) (295, 28) ((83, 80), 93) (((294, 96), 557), 40) (464, 34) (81, 177)

NOTE; Cell 290 is not in the xls, but should not affect your scripting solution. Open a ticket if you have any questions

## Solution:

1. The intersection point of two axes is the ASCII value of the character in the flag.
