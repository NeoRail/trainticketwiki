---
title: France
---

The SNCF ("Société National des Chemins de Fer") is the French national train company, which uses its own standard for domestic tickets.

## SNCF TGV Barcode Specification

This barcode does not have a public specification file available, and was reverse engineered.

### Notable Characteristics

|                |                      |
|----------------|---------------------:|
| Leading Bytes  |               `i0CV` |
| Length         | 131 bytes (constant) |
| Encoding       |       ISO/IEC 8859-1 |
| Signature      |                  N/A |


### Ticket Structure

!!! info "Offsets are number of bytes"

Field                    | Offset Start | Offset End | Length (bytes) | Format                          |
------------------------ | -----------: | ---------: | -------------: | ------------------------------- |
Magic Bytes              |            0 |          3 |              4 | `69 30 43 56` -> `i0CV` (fixed) |
Passenger Name Record    |            4 |          9 |              6 |                                 |
Ticket Number            |           10 |         18 |              9 |                                 |
Unknown                  |           19 |         22 |              4 | `31 32 31 31` -> `1211` (fixed) |
Traveller Date of Birth  |           23 |         32 |             10 | `%d/%m/%Y`                      |
Departure Station        |           33 |         37 |              5 |                                 |
Arrival Station          |           38 |         42 |              5 |                                 |
Train Number             |           43 |         47 |              5 |                                 |
Travel Date              |           48 |         52 |              5 | `%d/%m`                         |
Traveller SNCF ID        |           53 |         71 |             19 | 0-string if missing             |
Traveller Surname        |           72 |         90 |             19 | Left-space padded string        |
Traveller Forename       |           91 |        109 |             19 | Left-space padded string        |
Travel Class             |          110 |        110 |              1 |                                 |
Tariff Code              |          111 |        114 |              4 |                                 |
Return Travel Class      |          115 |        115 |              1 | 0-string if missing             |
Return Departure Station |          116 |        120 |              5 | Empty string if missing         |
Return Arrival Station   |          121 |        125 |              5 | Empty string if missing         |
Return Train Number      |          126 |        130 |              5 | 0-string if missing             |

### Kaitai Spec

The Kaitai Spec for this is also located on [GitHub](https://github.com/Fahrschein-Autismus/train-barcode-kaitai-spec/blob/main/sncf/sncf.ksy).

??? YAML Code

    ```yaml
    meta:
    id: barcode_sncf
    file-extension: bin
    encoding: "iso-8859-1"
    endian: le
    seq:
    - id: magic
        contents: [0x69, 0x30, 0x43, 0x56]
        doc: "`i0CV` are the four magic bytes identifying tickets issued by SNCF."
    - id: passenger_name_record
        type: str
        size: 6
        doc: "Passenger Name Record (assumedly)"
    - id: ticket_number
        type: str
        size: 9
        doc: "Ticker number"
    - id: unknown_data
        contents: [0x31, 0x32, 0x31, 0x31]
        doc: "Unknown Data"
    - id: traveller_dob
        type: str
        size: 10
        doc: "Traveller Date of Birth (format: `%d/%m/%Y`)"
    - id: departure_station
        type: str
        size: 5
        doc: "5-character departure Benerail station ID"
    - id: arrival_station
        type: str
        size: 5
        doc: "5-character arrival Benerail station ID"
    - id: train_number
        type: str
        size: 5
        doc: "5-digit train number (left-zero-padded)"
    - id: travel_date
        type: str
        size: 5
        doc: "Date of the travel (format: `%d/%m`)"
    - id: traveller_sncf_id
        type: str
        size: 19
        doc: "SNCF Traveller ID (Internal)"
    - id: traveller_surname
        type: str
        size: 19
        doc: "Surname of the traveller (left-space-padded)"
    - id: traveller_forename
        type: str
        size: 19
        doc: "Forename of the traveller (left-space-padded)"
    - id: travel_class
        type: str
        size: 1
        doc: "1-digit travel class (1, 2)"
    - id: tariff_code
        type: str
        size: 4
        doc: "Tariff Code"
    - id: travel_class_return
        type: str
        size: 1
        doc: "1-digit travel class (0, 1, 2)"
    - id: departure_station_return
        type: str
        size: 5
        doc: "5-character departure Benerail station ID"
    - id: arrival_station_return
        type: str
        size: 5
        doc: "5-character arrival Benerail station ID"
    - id: train_number_return
        type: str
        size: 5
        doc: "5-digit train number (left-zero-padded)"
    ```

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
