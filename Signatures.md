RSA signature : 0x90 0x78 0x00 0x00 len data

GetData: 0x90 0xCA 0x00 byte

ProcessDigitalKeyCommand: 0x90 0x7C 0x01 0x00 len data

ProcessDigitalKeyResponse:
Frame: 116 bytes, byte[2], byte[8], byte[106]
as expected, 116 byte response is broken down into [2][8][106]
header = frame[0]
tokenId = frame[1]
authCommand = frame[2]

Authentication:

Select

ProcessDigitalKeyCommand 1

ProcessDigitalKeyCommand 2

Reader requests: 0x25 long

Open/start:

Framing seems to be:
[3] [64] [2]
cmd data pad

cmd 1:
633301 b0352073dd3ccacdbdf4859b0f0480c0e4bf9cd79abed4a4a600d99cfd1d28bb 0000

cmd 2:
633301 1409f90f3c013d61b8eeb223156e723984b4c666438e4de9337d6d0eae93e215 0000

cmd 4:
633301 957f06ee1a85b0079fdb2b7feac6eb484fd1bf15812f45a6b664250bd217374a 0000

re-pair:

cmd 3:
633310 ab7c8fc2500c2c5a1f9f704ccd0a10a38e26bfb5a8ce3814f3ca5e2d87a36c95 0000

Card responses: 
64 byte response 
broken down into?
[3] [8] [53]
Open/start:

cmd 1:
343641 e87f76f4bcf2d152 db2fe8ad35e47def4a88510fbc40cd86d826908f5f5b106dde906e5fb33dbbb0730a0f67ce41e85f45ca574bd174793796e49a7743

cmd 2:
343641 e87f76f4bcf2d152 328e40b02a7172aaf938414c71b6e6e4f1efe28f8362840f73f0ebd5fe0d32f67d75442bf00c8ecff90a0edfe13ef34e88d55d1e5b

Second set of reader requests run after the first? 
Framing appears to be as above, but no data
[3] [2]
cmd pad

Always sends 633601 0000 and responds 34370000
