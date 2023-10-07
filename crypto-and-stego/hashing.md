# Hashing

Cryptographic hash functions play a pivotal role in various aspects of cybersecurity, including data integrity, authentication, and password storage. Hashing, in essence, is the process of converting data into a fixed-size string of characters, typically represented as a hexadecimal number. This transformation ensures that the resulting hash is unique to the input data.

## Hash Identification

***

### Online Tools

***

1. [Hashes.com](https://hashes.com/en/tools/hash\_identifier)
   * A versatile online tool for identifying hash types from provided samples.
2. [TunnelsUp Hash Analyzer](https://www.tunnelsup.com/hash-analyzer/)
   * An informative online resource for hash analysis and identification.
3. [OnlineHashCrack](https://www.onlinehashcrack.com/)
   * A web-based service that assists in identifying hash algorithms and cracking hashed passwords.
4. [CrackStation](https://crackstation.net/)
   * An online platform offering hash identification and decryption services for various hash types.

### Offline Tools

***

#### In Kali Linux

Use `hash-identifier`

```bash
hash-identifier
```

Calculate the SHA-1 hash (or other hash algorithms) of a file in Linux:

```bash
shasum $FILE
```

#### In Windows

Utilize `CertUtil` to calculate the hash of a file:

```bash
CertUtil -hashfile filename.ext
```
