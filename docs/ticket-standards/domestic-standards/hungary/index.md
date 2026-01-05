---
title: Hungary
---

## MÁV (Magyar Államvasutak)

This is used by domestic railway tickets/passes from MÁV as well as Volánbusz tickets.

This barcode does not have a public specification file available, and was reverse engineered.

### Characteristics

* Occurs both in PDF417 and Aztec format.
* Exists in different versions, the first byte being the version.
* Most of the payload is Gzip-compressed, starting with the standard Gzip header `0x1f8b0800000000000000`.
* Content is signed, signature is appended.
* String encoding uses UTF-8.
* Date/time values are encoded as seconds since 2017-01-01 00:00:00 CET (or 2016-12-31 23:00:00 UTC), with the exception
  of the traveler birth date.
* Uses seemingly random 32bit values as identifiers for ticket types, discounts, etc. Most of those codes haven't
  been identified and documented yet.

### Kaitai Spec

A Kaitai spec for versions 2-6 is located on [GitHub](https://github.com/NeoRail/train-barcode-kaitai-spec/blob/main/mav/mav.ksy).

### Related Work

* [MÁV train ticket barcode data extractor](https://github.com/pjuhasz/mav_train_ticket)


## MÁV Legacy Tickets

This was used by MÁV up to 2020.

This barcode does not have a public specification file available, and was reverse engineered.

### Characteristics

* QR code containing a hex string.
* The hex string is Zlib-compressed, starting with Zlib magic bytes `0x789C`.
* Decompression results in a UTF-8 encoded string.
    * The first 512 bytes are a hex string again, presumably a signature.
    * The second part is delimited by `!` into 32 fields (see table below).

### Content

Field | Format               | Content                        | Notes                                |
 ---: | -------------------- | ------------------------------ | ------------------------------------ |
0     | `~<number>`          | Ticket number                  |                                      |
1     |                      | Passenger name                 |                                      |
2     | `yyyy.MM.dd`         | Passenger birth date           |                                      |
3     | number               | Total price                    | in HUF                               |
4     | alpha-numberic code  | ?                              |                                      |
5     | `yyyy.MM.dd HH:mm`   | Begin of validity              |                                      |
6     | `yyyy.MM.dd HH:mm~v` | End of validity                |                                      |
7     | `MÁV <number>`       | Travel distance                |                                      |
8     | `-` separated string | Vias                           | `(-)` when empty                     |
9     |                      | Departure station name         |                                      |
10    |                      | Arrival station name           |                                      |
11    |                      | ?                              |                                      |
12    |                      | ?                              |                                      |
13    |                      | ?                              |                                      |
14    |                      | ?                              |                                      |
15    |                      | Train number                   | Numeric only, no train type prefix   |
16    | `1` or `2`           | Class                          |                                      |
17    | `yyyy.MM.dd~m`       | Day of travel                  |                                      |
18    |                      | Trafif or discount name        | e.g. "Teljesárú" (full price)        |
19    | `<number>~h`         | Ticket price                   | in HUF                               |
20    |                      | Departure station name         | possibly for seat reservation?       |
21    |                      | Arrival station name           |                                      |
22    | `yyyy.MM.dd`         | Day of travel                  |                                      |
23    | `HH:mm`              | Time of departure              |                                      |
24    |                      | ?                              |                                      |
25    |                      | ?                              |                                      |
26    |                      | Train number                   | Including product/category prefix    |
27    |                      | Coach number                   |                                      |
28    |                      | Seat number                    |                                      |
29    | number               | Price of reservation           | in HUF                               |
30    |                      | Name of the reservation ticket | e.g. "Pót- és helyjegy"              |
31    | `MÁV <number>`       | Travel distance                | not always present                   |
