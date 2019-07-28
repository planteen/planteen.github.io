---
layout: note
title: Reed-Solomon Codes
---

Log/antilog tables for GF(256) multiplication
---------------------------------------------

When working with Reed-Solomon codes, log/antilog tables are helpful to
calculate Galois field products by hand.

This PDF contains log/antilog tables for all 30 irreducible polynomials in
GF(256). 16 of these polynomials are primitive. Of special note, the primitive
polynomials 0x11D and 0x187 are most commonly used in Reed-Solomon codes. The
non-primitive polynomial 0x11B is used by the AES encryption algorithm and the
Intel CPU instruction GF2P8MULB. Non-primitive, irreducible polynomials can be
for Reed-Solomon codes, but some software does not support
non-primitive polynomials (such as MATLAB/Octave and Phil Karn's libfec).

[gf256_log_antilog.pdf](../assets/rs/gf256_log_antilog.pdf)

Primitive elements in GF(256)
------------------------------

A Reed-Solomon code generator polynomial requires selection of a primitive
element of GF(256). The 128 primitive elements of GF(256) are listed in the
following document.

[gf256_prim.pdf](../assets/rs/gf256_prim.pdf)

External Links
--------------

[GF(256) AES/0x11B log/antilog tables for all primitive elements](https://www.samiam.org/logtables.txt)

[Computation in finite fields](https://johnkerl.org/doc/ffcomp.pdf)

[Reed–Solomon codes for coders](https://en.wikiversity.org/wiki/Reed%E2%80%93Solomon_codes_for_coders)

[CCSDS 101.0-B-5 Reed-Solomon spec](https://public.ccsds.org/Pubs/101x0b5s.pdf)

[Reed-Solomon Encoders - Conventional vs Berlekamp's Architecture](https://ntrs.nasa.gov/archive/nasa/casi.ntrs.nasa.gov/19830008870.pdf)
