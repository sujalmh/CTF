# What Are You Doing In My Swamp?

This challenge is like ogres, it has layers

### Files: layers.jpg

## Solution:

1. The image is corrupted, using hexedit to correct the bytes `FF D8 FF` in the beginning and `FF D9`
<p align="center">
  <img src="./What Are You Doing In My Swamp/layers_corrected.png" alt="result" width="75%">
</p>
2. Using Stegseek to brute force passphrase for Steghide. Found passphrase is `layers`
<p align="center">
  <img src="./What Are You Doing In My Swamp/stegseek.png" alt="result" width="75%">
</p>
3. `secret_message.txt` has the flag GFXGU{LtIvh_zIv_oRpv_lmrOmh}, which on Atbash decoding gives flag.
<p align="center">
  <img src="./What Are You Doing In My Swamp/layers_flag.png" alt="result" width="75%">
</p>

### Flag: TUCTF{OgRes_aRe_lIke_oniLns}

---

# State of the Git

All the cool kids are embracing state of the art IAC technology, and we are rushing to catch up! We have a new system that we are testing out, but we are not sure how secure it is. Can you check it out for us?

### Files: tuctf-devops-2023.tar.gz

## Solution:

1. Extracting files, and intializating git.
2. git log > logs.txt, saving logs to file.
3. There are many branches in the repo. `git branch`
4. The first commit is made to dev branch, `git reset 4cd927392f6f9adcd950afae9cba8a77879ed72a` `git show`
5. the Flag is base64 encoded in terraform.tfstate, VFVDVEZ7NzNycjRmMHJtX1M3QTczLTF5XzUzY3IzNzV9Cg==
<p align="center">
  <img src="./State of the Git/git_b64.png" alt="result" width="75%">
</p>

### Flag: TUCTF{73rr4f0rm_S7A73-1y_53cr375}
