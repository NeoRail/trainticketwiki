---
title: Spain
---

Tickets from Spanish operators Renfe and Ouigo ES have been observed standalone
as well as in the common ADIF container.

## ADIF Container

Defined in §7.3.2.5 of the ADIF Network Statement 2026 (available on https://www.adif.es, but currently
only from Spanish IP addresses).

### Characteristics

* Uses Aztec format.
* Fixed-length 516 byte ASCII content.
* Uses UIC station codes (with domestic ones using a '00' instead of '71' country prefix).

### Kaitai Spec

A Kaitai spec for this can be found on [GitHub](https://github.com/NeoRail/train-barcode-kaitai-spec/blob/main/spain/spain.ksy).
The `operator_use` field contains the Renfe or Ougio ticket barcodes described below.

## Renfe

### Characteristics

* Uses QR or DataMatrix codes when occurring outside of the ADIF container.
* Fixed-length ASCII content in two variants (with or without "Combinado Cercanias" suffix)
* Uses UIC station codes without the country prefix, ie. this only works domestically.

### Kaitai Spec

A Kaitai spec for this can be found on [GitHub](https://github.com/NeoRail/train-barcode-kaitai-spec/blob/main/spain/renfe.ksy).

## Ouigo ES

This is presumably the same format as used by Ouigo in France. Payload is Base64-encoded high-entropy binary of an unknown format.
