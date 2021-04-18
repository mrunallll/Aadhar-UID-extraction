# aadhar-uid
SRGAN based Aadhar UID Extraction and Secure Masking technique

We often submit scanned aadhar card documents to banks, government offices etc. Have we ever wondered how they handle our aadhar card documents? 
This is about extracting relevant information from the aadhar cards - 12 digit UID (Unique Identification Number/Aadhar Number)

The solution to this lies in the following 4 steps:

1. OCR of real scanned aadhar photos/documents 
3. Extracting the 12 digit UID (aadhar number)
4. Validation of extracted aadhar number
5. Secure Masking of UID (aadhar number)

**OCR of aadhar photos**
This is the simplest step done using Tesseract. (pytesseract library in python)

**Extraction**
This involves image preprocessing techniques for starters. If the correct UID is still not being recognized due to bad image scan quality, 
we use the ESRGAN (Enhanced Super Resolution Generative Adversarial Network) technique to enhance the quality of image.

For more details aout ESRGAN, refer:
https://openaccess.thecvf.com/content_ECCVW_2018/papers/11133/Wang_ESRGAN_Enhanced_Super-Resolution_Generative_Adversarial_Networks_ECCVW_2018_paper.pdf

**Validation/Verification of Aadhar UIDs**
The GoI has created the 12 digit aadhar UIDs such thatthe last digit is a checksum which can be calculated using Verhoeff algorithm.
_Verhoeff Algorithm uses permutation and multiplication tables for validation & verification of checksum_
We also delete the invalid non-matching UIDs that are generated using regex.

**Secure Masking of UIDs**
We use opencv to mask/balck out the aadhar number using the same bounding boxes as for extraction.
