# Stego of Images

Steganography, the art of concealing information within digital media, allows for the covert embedding of data within files like images without leaving any visible traces. Within the realm of steganography, image steganography stands as a crucial subfield, focusing on the discreet integration of information within image files. The primary objective? Ensuring that the modified image maintains its visual integrity, remaining virtually indistinguishable from the original to avoid detection.

### The Practical Applications of Image Steganography

***

#### Covert Communication

* **Malicious Intent:** Cyber adversaries leverage image steganography to clandestinely convey instructions, malware, or pilfered data within innocuous images, skillfully circumventing conventional security measures.

#### Data Exfiltration

* **Insider Threats:** Internal actors may exploit image steganography to surreptitiously siphon sensitive corporate data, posing a substantial risk to organizations that rely on data confidentiality.

#### Watermarking and Copyright Protection

* **Legitimate Use:** Image steganography isn't solely a tool of malfeasance. It serves lawful purposes such as watermarking images for copyright safeguarding or discreetly embedding marks for the authentication of authenticity.

### Extracting Hidden Data from Images

***

#### JPEG Images

```bash
$ steghide extract -sf $IMAGE
$ stegoveritas -steghide $IMAGE
$ stegoveritas -exif -steghide $IMAGE
$ binwalk -e $IMAGE
```

#### PNG Images

Utilizing `zsteg`

```bash
$ zsteg $IMAGE
```

#### Image Metadata

Extract data from image metadata using `exiftool`:

```bash
$ exiftool $IMAGE
```

#### Password-Protected Images

For extracting data from password-protected images

```bash
$ steghide extract -sf $IMAGE 
$ stegcracker $IMAGE /usr/share/wordlists/rockyou.txt
```
