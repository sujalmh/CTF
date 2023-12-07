# Keyboard Cipher

I designed an algorithm to encrypt a message using my keyboard. No one can decrypt it without any information about my algorithm. Note: Wrap the flag in TUCTF{}.

## Solution:

1. The encoded file is in Hex, after decoding it gives base64 string.
2. Decoding base64 gives ascii string.
3. The characters form a pattern, the letters surround a key on the keyboard

### Flag: TUCTF{tUCTfstXhAKsLH}

---

# Table Encryption

You can't crack my file! I am the exclusive owner of the encryption key!

## Solution:

1. The file looks like XOR encrypted file.
2. Using xor-decrypt tool to find the key for XOR encryption.
3. Password is found Emoji Moring Sta `python3 xor-decrypt.py -i "table_encryption.xml.enc" -o "out.txt" -m 32 -f 32 -d`
<p align="center">
  <img src="./Table Encoding/table_enc.png" alt="result" width="75%">
</p>

### Flag: TUCTF{x0r_t4bl3s_R_fun!!!11!}

---

# Custom ECB Cipher

I have designed a simple algorithm which I believe it's secure. I am confident you cannot compromise my message with the x value.

## Solution:

1. Reverse the given code for encryption.
2. Pick the decoded text from brute force which only has ascii characters.

```python
def reverse_convert(msg, x):
    for i in range(3):
        msg = msg ^ msg >> 14
    for i in range(1):
        msg = msg ^ msg << 20 & 2186268085
    for i in range(1):
        msg = msg ^ msg << 13 & 275128763
    for i in range(3):
        msg = msg ^ msg >> x
    return msg

def reverse_transform(hex_message, x):
    message = bytes.fromhex(hex_message)
    assert len(message) % 4 == 0
    new_message = b''
    for i in range(int(len(message) / 4)):
        block = message[i * 4: i * 4 + 4]
        block = number.bytes_to_long(block)
        # Reverse the conversion
        block = reverse_convert(block, x)
        block = number.long_to_bytes(block, 4)
        new_message += block
    return new_message
```

### FLag: TUCTF{sRta^s90s-#VgsnzPsta-TjLx7s8Txgs-\*Ko}

---

# Never Ending Crypto: Taylor's Version

The return of the annual Never Ending Crypto Challenge, but this time, it's Taylor's version!

## Solution

1. It was binary characters replaced by Taylor and Swift. `0` was `Taylor` and `1` was `Swift`.
2. Some challenges were direct substitution, while others were shifted by some offset.
3. Completing all challenges gives flag.
