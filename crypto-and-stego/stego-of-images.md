# Stego of Images

Steganography is the art of concealing information within digital media, such as images, without leaving any visible traces. Cybersecurity professionals often use specialized tools to reveal hidden data within images. Here are some commands for extracting hidden data from image files:

#### Steghide

Extract Hidden Data from .jpg Image:

```shell
$ steghide extract -sf $IMAGE
```

#### Stegoveritas

Extract Hidden Data from .jpg Image:

```shell
$ stegoveritas -steghide $IMAGE
```

Extract Hidden Data from .jpg Image:

```shell
$ stegoveritas -exif -steghide $IMAGE
```

#### Binwalk

Extract Hidden Data from .jpg Image:

```shell
$ binwalk -e $IMAGE
```

#### Zsteg

Extract Hidden Data from .png Image:

```shell
$ zsteg $IMAGE
```

#### Exiftool

Extract Hidden Data from Image Metadata:

```shell
$ exiftool $IMAGE
```

#### Steghide (Password-Protected)

Extract Data from Password-Protected Image:

```shell
$ steghide extract -sf $IMAGE
$ stegcracker $IMAGE /usr/share/wordlists/rockyou.txt
```
