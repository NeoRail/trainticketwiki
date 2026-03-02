---
title: United Kingdom
---

# RSP-6

The RSP-6 format used in the UK was initially [reverse engineered](https://eta.st/2023/01/31/rail-tickets.html),
but the [official documentation](https://magicalcodewit.ch/rsp-specs/) meanwhile also became available under
Freedom of Information Act requests.

## Characteristics

* Uses the Aztec format.
* Content is ASCII, starting with "06", additional 13 clear-text bytes and a Base26 encoded RSA-encrypted payload.

## Related Work

* [RSP-6 decoder implementation](https://git.eta.st/eta/rsp6-decoder)
