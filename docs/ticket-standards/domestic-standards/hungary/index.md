---
title: Hungary
---

# MÁV (Magyar Államvasutak)

This is used by domestic railway tickets/passes from MÁV as well as Volánbusz tickets.

This barcode does not have a public specification file available, and was reverse engineered.

## Characteristics

* Occurs both in PDF417 and Aztec format.
* Exists in different versions, the first byte being the version.
* Most of the payload is Gzip-compressed, starting with the standard Gzip header 0x1f8b0800000000000000.
* Content is signed, signature is appended.
* String encoding uses UTF-8.
* Date/time values are encoded as seconds since 2017-01-01 00:00:00 CET (or 2016-12-31 23:00:00 UTC), with the exception
  of the traveler birth date.
* Uses seemingly random 32bit values as identifiers for ticket types, discounts, etc. Most of those codes haven't
  been identified and documented yet.

## Kaitai Spec

A Kaitai spec for versions 2-6 is located on [GitHub](https://github.com/NeoRail/train-barcode-kaitai-spec/blob/main/mav/mav.ksy).

## Related Work

* [MÁV train ticket barcode data extractor](https://github.com/pjuhasz/mav_train_ticket)
