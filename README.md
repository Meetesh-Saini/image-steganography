# image-steganography
A tool to hide data in image.  

Data is protected with AES-GCM. First data is encrypted with the key and then it is injected into the image.  
Since GCM requires nonce, the output for same image, same unencrypted data and same key will be different everytime.  

## Installation
```
git clone https://github.com/Meetesh-Saini/image-steganography.git  
```

## Examples 
### Text to hide
```
from image_steganography import Hide  
detective = Hide()  
detective.inject("input.png", "output.png", "secret_key_128_192_256_bits_long".encode(), "my text to hide 😊️")  
```
### Extracting hidden text  
```
from image_steganography import Hide  
detective = Hide()  
text = detective.eject("input.png", "secret_key_128_192_256_bits_long".encode())  
print(text)  
```
###  Hiding binary file (png, mp4, pdf, etc.)
```
from image_steganography import Hide  
detective = Hide()  
with open("input.mp4", "rb") as f:  
    file_data = f.read()  
detective.inject("input.png", "output.png", "secret_key_128_192_256_bits_long".encode(), file_data)  
```
### Extracting hidden file (any binary data)
```
from image_steganography import Hide  
detective = Hide()  
file_data = detective.eject("input.png", "secret_key_128_192_256_bits_long".encode(), toDecode=False)  
with open("output.mp4", "wb") as f:
    f.write(file_data)
```
