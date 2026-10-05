---
title: France
---

The SNCF ("Société National des Chemins de Fer") is the French national train company, which uses its own standard for domestic tickets.

## SNCF TGV Barcode Specification

This barcode does not have a public specification file available, and was reverse engineered.

### Notable Characteristics

|                |                      |
|----------------|---------------------:|
| Format         |      Aztec or PDF417 |
| Length         | 131 bytes (constant) |
| Encoding       |       ISO/IEC 8859-1 |
| Signature      |                  N/A |

### Station Codes

Stations use a five letter upper-case ASCII code, with the two leading letter being an ISO 3166-2 alpha 2 country code.

* [Wikidata P8181](https://www.wikidata.org/wiki/Property:P8181)
* [Trainline stations.csv](https://github.com/trainline-eu/stations) column "Sncf Id"

!!! info "Note that these are different codes than the [Benerail codes](https://www.wikidata.org/wiki/Property:P8448) used e.g. by Thalys that have the same format."

### Tariff Codes

A full list of used tariff codes is unknown, the below are values observed in the wild.

| Code  | Description                                                                 |
|-------|-----------------------------------------------------------------------------|
| CF00  | "Ayant Droit Résa Payante", "Ayant Droit avec fichet" - 100% staff discount |
| CF90  | "Ayant Droit 90%", "Ayant Droit sans fichet" - 90% staff discount           |
| CJ11  | "CARTE JEUNE"                                                               |
| CW00  | "CARTE AVANTAGE ADULTE"                                                     |
| CW11  | "CARTE AVANTAGE ADULTE"                                                     |
| CW12  | "NO FLEX CARTE AVANTAGE ADULTE"                                             |
| CW25  | "CARTE AVANTAGE ADULTE"                                                     |
| EF11  | "CARTE ENFANT+" (parent)                                                    |
| EF99  | "CARTE ENFANT+" (child)                                                     |
| FA11  | "BUSINESS PREMIERE"                                                         |
| FF40  | "CARTE FORFAIT LIGNE CLASSIQUE"                                             |
| FF70  | "CARTE FORFAIT"                                                             |
| FF98  | "BILLET ABONNEMENT FORFAIT"                                                 |
| FZ30  | Loyalty card                                                                |
| FZ41  | "MAX ACTIF PLUS"                                                            |
| FZ71  | "MAX ACTIF"                                                                 |
| FZ94  | "BILLET MAX ACTIF"                                                          |
| HC16  | "MAX JEUNE" - Formerly called TGVMax                                        |
| IR00  | "INTERRAIL CONTINGENTÉ 2ÈME CLASSE"                                         |
| IR01  | "INTERRAIL NON CONTINGENTÉ 2ÈME CLASSE"                                     |
| JE00  | "CARTE AVANTAGE JEUNE"                                                      |
| JR11  | "PREM's" occurs together with a loyalty program number in the PDF           |
| LB00  | "CARTE LIBERTE"                                                             |
| LB11  | "TARIF LIBERTE"                                                             |
| NU44  | "Billet illico PROMO VACANCES 40%"                                          |
| NV30  | "LIBERTIO’ JEUNES TRAIN JAUNE"                                              |
| NW26  | "BILLET ILLICO LIBERTE SEMAINE 25%"                                         |
| PR11  |                                                                             |
| PX01  | "TARIF NORMAL RÉGIONAL"                                                     |
| PX05  | "DIGITAL TARIF"?                                                            |
| SE00  | "CARTE AVANTAGE SENIOR"                                                     |
| SE11  | "BILLET CARTE AVANTAGE SENIOR"                                              |
| SR50  | "Carte Senior"                                                              |
| empty | not operated by SNCF

### Kaitai Spec

The Kaitai Spec for this is also located on [GitHub](https://github.com/Fahrschein-Autismus/train-barcode-kaitai-spec/blob/main/sncf/sncf.ksy).

## Ouigo

Long-distance services operated by Ouigo use a different barcode.

This barcode does not have a public specification available, nor has it been reverse engineered.

### Characteristics

* Uses Aztec format.
* Contains a base64 encoded 174 byte fixed size high entropy binary content.

## SNCF TER Tickets

Depending on the region TER services either use the following format or [UIC DOSIPAS](../../uic-standards/dosipas.html).

This barcode does not have a public specification available, and was reverse engineered.

### Characteristics

* Uses Aztec format.
* Fixed size, 686 bytes.
* Contains a binary signature and ASCII content.
* Uses the same station and tariff codes as the TGV ticket barcodes.

### Kaitai Spec

The Kaitai spec for this is located on [GitHub](https://github.com/Fahrschein-Autismus/train-barcode-kaitai-spec/blob/main/sncf/sncf-ter.ksy).
