# A.R.K. 1

One sheep, two sheep, three sheep. (Note: to speed up the process, only include entries containing "sheep" in your attempts) Flag is in the format TUCTF{<password>} (don't include the brackets)

## Solution:

1. Using `file sheep` to get the file type. It is OpenSSH private key
2. Using john-the-ripper to crack the private key
3. Creating hash of the file. `python3 ssh2john.py ../../../sheep > ../../../sheep.hash`
4. Writing python code to get passwords containing "sheep"
5. Using wordlist to crack sheep.hash `./john ../../../sheep.hash --wordlist="../../../sheep.txt"`

```python
input_file_path = "rockyou.txt"
output_file_path = "sheep.txt"


with open(input_file_path, "r", encoding="latin-1") as input_file, open(output_file_path, "w", encoding="utf-8") as output_file:

    for line in input_file:
        word = line.strip()
        if "sheep" in word:
            output_file.write(word + "\n")

print(f"Passwords with 'sheep' written to {output_file_path}")
```

### Flag: TUCTF{baabaablacksheep}

---

# A.R.K. 2

Woof woof bark bark (Note: to speed up the process, only include entries containing "dog" in your attempts)

## Solution:

1. The file is Keepass password database 2.x KDBX
2. Using john-the-ripper to crack Keepass password database KDBX file
3. Creating hash of the file. `./keepass2john ../../../woof > ../../../woof.hash`
4. Writing python code to get passwords containing "dog"
5. Using wordlist to crack woof.hash `./john ../../../sheep.hash --wordlist="../../../sheep.txt"`
6. The password to keepass database is `wholetthedogsout`. Using keepass to open kdbx file.
7. History shows `realFlag`, which can be found in string field.

```python
input_file_path = "rockyou.txt"
output_file_path = "dog.txt"


with open(input_file_path, "r", encoding="latin-1") as input_file, open(output_file_path, "w", encoding="utf-8") as output_file:

    for line in input_file:
        word = line.strip()
        if "dog" in word:
            output_file.write(word + "\n")

print(f"Passwords with 'dog' written to {output_file_path}")
```

<p align="center">
  <img src="./ARK 2/ark2_flag.png" alt="result" width="75%">
</p>

### Flag: TUCTF{K3eP_M4_Pa$s_rE4L_SaF3}

---

# A.R.K. 3

Meowdy. (Note: to speed up the process, only include entries containing "meow" in your attempts)

## Solution:

1. The file is Mac OS X Keychain File
2. Using john-the-ripper to crack Keychain File
3. Creating hash of the file. `python3 keychain2john.py ../../../meow > ../../../meow.hash`
4. Writing python code to get passwords containing "meow"
5. Using wordlist to crack woof.hash `./john ../../../meow.hash --wordlist="../../../meow.txt"`
6. The password to Keychain File database is `coolcatmeow`.
7. Using chainbreaker to open file. `chainbreaker -a ./meow --password=coolcatmeow` shows database.
8. History shows `realFlag`, which can be found in string field.

```python
input_file_path = "rockyou.txt"
output_file_path = "meow.txt"


with open(input_file_path, "r", encoding="latin-1") as input_file, open(output_file_path, "w", encoding="utf-8") as output_file:

    for line in input_file:
        word = line.strip()
        if "meow" in word:
            output_file.write(word + "\n")

print(f"Passwords with 'meow' written to {output_file_path}")
```

<p align="center">
  <img src="./ARK 3/meow.png" alt="result" width="75%">
</p>

### Flag: TUCTF{k3YCh41ns_AR3_sUp3r_c00L}

---

# A.R.K. 4

What does the fox say?

## Solution

1. The given file is firefox browser data.
2. Replacing password files in a new profile, gives flag stored in passwords in the browser.
<p align="center">
  <img src="./ARK 4/ark4_flag.png" alt="result" width="75%">
</p>

### Flag: TUCTF{B3w4R3_7h3_f1r3_4nd_7h3_f0x}

---

# Silly Registry

Everything about this registry is silly!

chal.tuctf.com:30003

## Solution:

1. The given registry is a Docker container.
2. Username of the container is `username` and Password to the container is `password`.
3. Using https://book.hacktricks.xyz/network-services-pentesting/5000-pentesting-docker-registry, download one of the blobs containing flag.

### Flag: TUCTF{my_51lly_53cr37_15_54f3_w17h_y0u}

---

# Secret Agent

Are you fit to be a secret agent?

nc chal.tuctf.com 30012

## Solution:

1. First challenge, had the key from the movie Kingsman: Secret Service `Oxfords, not brogues.` It gives key to the next round. `good_job_agent1089`
2. Second challenge Contained distance between all cities and to solve shortest path between two cities. This gives an encoded text `⠥⠞⠀⠞⠉⠀⠎⠊⠋⠀⠍⠁⠀⠵⠁⠀⠝⠊⠀⠺⠊⠛⠀⠇⠇⠊⠀⠕⠉⠀⠍⠀⠑⠀⠃⠀⠅⠉⠁⠀⠛⠁⠀⠝⠊⠁`

```python
import networkx as nx

distances = {
    ('Attaya','Charity'):3,     ('Attaya','Delato'):5,    ('Attaya','Belandris'):10,    ('Charity', 'Emell'): 2,
    ('Charity', 'Belandris'): 8,    ('Charity', 'Delato'): 1,    ('Charity', 'Haphsa'): 3,    ('Charity', 'Flais'): 8,
    ('Leter', 'Osiros'): 3,    ('Leter', 'Rhenora'): 10,    ('Emell', 'Gevani'): 5,    ('Emell', 'Iyona'): 3,
    ('Emell', 'Flais'): 5,    ('Gevani', 'Jolat'): 8,    ('Gevani', 'Iyona'): 1,    ('Gevani', 'Haphsa'): 6,
    ('Iyona', 'Jolat'): 15,    ('Iyona', 'Leter'): 4,    ('Iyona', 'Kepliker'): 3,    ('Rhenora','Notasto'):2,
    ('Rhenora','Shariot'):1,    ('Notasto','Shariot'):7,    ('Delato', 'Flais'): 5,    ('Delato', 'Belandris'): 3,
    ('Delato', 'Iyona'): 5,    ('Belandris', 'Jolat'): 15,    ('Belandris', 'Gevani'): 8,    ('Belandris', 'Emell'): 1,
    ('Osiros', 'Shariot'): 8,    ('Osiros', 'Rhenora'): 6,    ('Jolat', 'Osiros'): 7,    ('Jolat', 'Leter'): 4,
    ('Jolat', 'Kepliker'): 5,    ('Haphsa','Iyona'):8,    ('Haphsa','Kepliker'):7,    ('Haphsa','Melyphora'):8,
    ('Haphsa','Queria'):10,    ('Haphsa','Delato'):1,    ('Flais','Gevani'):3,    ('Flais','Iyona'):3,
    ('Flais','Haphsa'):1,    ('Kepliker','Osiros'):2,    ('Kepliker','Leter'):5,    ('Kepliker','Partamo'):6,
    ('Kepliker','Queria'):7,    ('Kepliker','Melyphora'):5,    ('Kepliker','Delato'):2,    ('Melyphora','Partamo'):4,
    ('Melyphora','Shariot'):11,    ('Melyphora','Queria'):1,    ('Partamo','Osiros'):1,    ('Partamo','Rhenora'):5,
    ('Partamo','Shariot'):9,    ('Queria','Partamo'):1,    ('Queria','Shariot'):10,    ('Queria','Rhenora'):6
}

# Create a graph
G = nx.DiGraph()

# Add edges with weights to the graph
for (city1, city2), distance in distances.items():
    G.add_edge(city1, city2, weight=distance)

# Find the shortest path from Attaya to Shariot
shortest_path = nx.shortest_path(G, source='Attaya', target='Shariot', weight='weight')

# Calculate the total weight of the shortest path
total_weight = sum(distances[shortest_path[i], shortest_path[i+1]] for i in range(len(shortest_path)-1))

print("Shortest Path from Attaya to Shariot:", shortest_path)
print("Total Weight:", total_weight)
```

3. `⠥⠞⠀⠞⠉⠀⠎⠊⠋⠀⠍⠁⠀⠵⠁⠀⠝⠊⠀⠺⠊⠛⠀⠇⠇⠊⠀⠕⠉⠀⠍⠀⠑⠀⠃⠀⠅⠉⠁⠀⠛⠁⠀⠝⠊⠁` decodes to `UT TC SIF MA ZA NI WIG LLI OC M E B KCA GA NIA`, which is Little Endian encoded. Decoding gives `TUCTFISAMZAINGIWILLCOMEBACKAGAIN`.
4. Last stage gives the flag.
