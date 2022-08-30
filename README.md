# hyundai-keycard
Hyundai keycard information and eventually implementation.

AID: A000000350434B010101

RID: A000000350 - Hyundai Motor Company

RPclient: Appears to be some kind of FIDO server settings? Comments as follows in this file.
#####Hyundai Dev#####
#ServerURL= https://dev1.roundee.com/FIDO_Server_kmc/
#RequestURL= processUafRequest.jspx?site=H101_W
#ResponseURL= processUafResponse.jspx?site=H101_W
#ServerURL= https://mpass.hmc.co.kr/FIDO_Server_hmc/
ServerURL= https://dev1.roundee.com/FIDO_Server_hmc/
RequestURL= processUafRequest.jspx?site=HMC_MTALK
ResponseURL= processUafResponse.jspx?site=HMC_MTALK

## Dev Autoway SiteID ##
## HyunDai : HMC_AUTOWAY
## KIA : KMC_AUTOWAY 

## Dev MTalk SiteID ##
## HyunDai : HMC_MTALK
## KIA : KMC_MTALK

## Dev HKMC SiteID ##
## HyunDai : H101_W
## KIA : K101_W

#####HyunDai MPass Real#####
#ServerURL= https://mpass.hmc.co.kr/FIDO_Server_hmc/
##ServerURL= https://mpass.kia.co.kr/FIDO_Server_kmc/
#RequestURL= processUafRequest.jspx?site=HMC_AUTOWAY
#ResponseURL= processUafResponse.jspx?site=HMC_AUTOWAY
### Real Autoway SiteID ###
## Hyundai : HMC_AUTOWAY ##
## KIA : KMC_AUTOWAY ##
### Real MTalk SiteID ###
## Hyundai : HMC_MTALK ##
## KIA : KMC_MTALK ##
############################

#####HyunDai HCCC Real#####
#ServerURL= https://finfido.autoever.com/FIDO_Server/
#RequestURL= processUafRequest.jspx?site=HCC
#ResponseURL= processUafResponse.jspx?site=HCC
## Real HCCC SiteID ##
## HyunDai : HCC, HCS, HCI
############################


##Dream##
#ServerURL= https://fido.dreamsecurity.com:18443/MagicFIDO_RPServer/
#ServerURL= https://fido.dreamsecurity.com:18443/MagicFIDO2Server/
#RequestURL= processUafRequest.jspx?site=www.da.com
#ResponseURL= processUafResponse.jspx?site=www.da.com


Looks like possible RSA from com.hyundai.digitalkey.securestorage.usim.cmd.RsaSignatureCommand. 

Appears to be some kind of certificate for phone keys that is uploaded when a key is paired. I suspect something goes on via Bluetooth.

usim command APDUs: 

RSA signature : 0x90 0x78 0x00 0x00 len data

GetData: 0x90 0xCA 0x00 byte

ProcessDigitalKeyCommand: 0x90 0x7C 0x01 0x00 len data

ProcessDigitalKeyResponse:
Frame: 116 bytes, byte[2], byte[8], byte[106]
as expected, 116 byte response is broken down into [2][8][106]
header = frame[0]
tokenId = frame[1]
authCommand = frame[2]

Dream Security Co appears to be a Korean security device manufacturer

roundee.com expired at some point it appears

https://mpass.hmc.co.kr/FIDO_Server_hmc/processUafRequest.jspx?site=HMC_MTALK gives no response as we obviously don't have a payload
