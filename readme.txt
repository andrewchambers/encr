ENCR(1)                   BSD General Commands Manual                  ENCR(1)

NAME
     encr — encrypt, authenticate and decrypt streams of data using a shared
     key.

SYNOPSIS
     encr [-g] [-d] [-k keyfile]

DESCRIPTION
     encr encrypts or authenticates and decrypts (with -d) using a shared
     96-byte key keyfile (provided via -k, or generated with -g and -k). Input
     is passed via stdin, and output is printed to stdout.  encr buffers data
     into segments for processing and blocks if not enough data is provided,
     it is unsuitable for interactive encryption/decryption.

     encr protects confidentiality with AES-256 CTR encryption and checks
     integrity/authenticity using HMAC with the SHA256 hash function.  encr
     will not pass unauthenticated data to stdout, and aborts when given an
     unauthenticated, reordered or truncated data stream.

     encr aborts if keyfile is world accessible.

EXIT STATUS
     The encr utility exits 0 on success, and >0 if an error occurs.

EXAMPLE
     generate a random key file:
     $ encr -g -k ./secret.key

     encrypt a plain text:
     $ encr -k ./secret.key < plain.txt > cipher.txt

     decrypt a cipher text:
     $ encr -d -k ./secret.key < cipher.txt > plain.txt


BSD                             March 17, 2017                             BSD
