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
polynomials 0x11D and 0x187 are first since they are most commonly used in
Reed-Solomon codes. The non-primitive polynomial 0x11B is used by the AES
encryption algorithm and the Intel CPU instruction GF2P8MULB. Non-primitive,
irreducible polynomials can be used with finite fields for Reed-Solomon codes,
but many libraries and programs do not support non-primitive polynomials (such
as MATLAB/Octave and Phil Karn's original libfec).

[gf256_log_antilog.pdf](../assets/rs/gf256_log_antilog.pdf)

Primitive elements in GF(256)
------------------------------

A Reed-Solomon code generator polynomial requires selection of a primitive
element of GF(256). The 128 primitive elements of GF(256) are listed in the
following document.

[gf256_prim.pdf](../assets/rs/gf256_prim.pdf)

