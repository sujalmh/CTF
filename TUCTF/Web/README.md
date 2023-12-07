# PHP Practice

Have you ever seen an image on a website, and wished you could use the link to view it from a different domain? Me neither, but I needed web dev practice so I implemented it anyways! Give it a try -- Feed my site a link and it'll load your file!

https://php-practice.tuctf.com

## Solution:

1. Find .htacess in the root directory (guessing common files in default directories) file:///var/www/html/.htaccess
<p align="center">
  <img src="./PHP Practice/payload.png" alt="result" width="75%">
</p>

2. .htaccess shows `gcfYAvzsbyxV.txt` is in the root
<p align="center">
  <img src="./PHP Practice/htaccess.png" alt="result" width="75%">
</p>

3. Using `file:///var/www/html/gcfYAvzsbyxV.txt` as payload, gives flag.
<p align="center">
  <img src="./PHP Practice/php_practice_flag.png" alt="result" width="75%">
</p>

### Flag: TUCTF{th1s_i5_my_secr3t_l0c@l_f1le!}

# PNG and Jelly Sandwich

It wasn't that hard at all, I even did it all with open-source software!

## Solution:

1. It uses a version of ImageMagick vulnerable to CVE-2022-44268. When it parses a PNG image (e.g., for resize), the resulting image could have embedded the content of an arbitrary remote file. <a src="https://github.com/Sybil-Scan/imagemagick-lfi-poc">Payload generator</a>
2. output filenames are in the format IM-{unix seconds}.{unix milliseconds}.png
