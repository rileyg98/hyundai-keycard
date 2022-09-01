**Authentication flow:**

Select - returns a Header and UID

ProcessDigitalKeyCommand 633301

ProcessDigitalKeyCommand 633601


**Pairing flow:**

Select - returns current UID, this gets reset during the pairing.

ProcessDigitalKeyCommand 633310

ProcessDigitalKeyCommand 633401


**ProcessDigitalKeyCommand subcmd set:**

63 33 01:
Used in authentication. Takes 32 bytes of data and tyo bytes of padding as follows:
[32] [2]
Padding is 00 00 in all instances seen. 

63 36 01:
Part 2 of authentication. Does not take data, only two bytes of 00 00 padding. 

63 33 10:
Part 1 of pairing. Takes [32][2] 32 bytes of data and 2 00 of padding. 

63 34 01:
Part 2 of pairing. Takes [101][2]. Unknown data? 2x 00 padding.


**DigitalKeyResponse subcmd set:**

34 36 41:
Response to 63 33 01 ProcessDigitalKeyCommand. Response is [8][53]. [8] is the UID found in the card select. 53 is some kind of signature data. Unknown as yet. 

34 37 00:
Response to 63 36 01 ProcessDigitalKeyCommand. Response is 00 in all instances. 
Also used to respond to 63 34 01 ProcessDigitalKeyCommand. 

34 34 xx:
Response to 63 33 10 ProcessDigitalKeyCommand. 32 byte response. Could this be a public key? 

**Select Response**

34 33 41:
TokenID after this as per the decompiled Hyundai app. [8][2] with 0000 padding in [2].
