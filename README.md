Image Encryption and Decryption Tool

This project provides a simple tool for encrypting and decrypting images using basic pixel manipulation techniques. Each pixel value in the image is modified by a user-defined key to ensure the image is securely transformed.

Features
Encrypt Images: Modify the pixel values of an image by adding a specified key to each pixel, resulting in an encrypted image.
Decrypt Images: Reverse the encryption by subtracting the specified key from each pixel to retrieve the original image.

How It Works
Encryption: Each pixel value in the image is increased by a user-defined key. The resulting pixel values are wrapped around using modulo 256 to stay within the valid range (0-255).
Decryption: Each pixel value in the encrypted image is decreased by the same key used for encryption. The resulting pixel values are again wrapped around using modulo 256.

Prerequisites
Python 3.x
Pillow (Python Imaging Library fork)
NumPy

Installation
Clone the Repository:

git clone https://github.com/your-username/image-encryption-tool.git
cd image-encryption-tool

Install Dependencies:
pip install pillow numpy

Usage
Encrypt an Image:
from encryption_tool import encrypt_image
encrypt_image('input_image.png', 'encrypted_image.png', key=123)

Decrypt an Image:

from encryption_tool import decrypt_image
decrypt_image('encrypted_image.png', 'decrypted_image.png', key=123)

Example
from PIL import Image
import numpy as np

def encrypt_image(image_path, output_path, key):
    img = Image.open(image_path)
    img_array = np.array(img)
    encrypted_array = (img_array + key) % 256
    encrypted_img = Image.fromarray(encrypted_array.astype('uint8'))
    encrypted_img.save(output_path)

def decrypt_image(image_path, output_path, key):
    img = Image.open(image_path)
    img_array = np.array(img)
    decrypted_array = (img_array - key) % 256
    decrypted_img = Image.fromarray(decrypted_array.astype('uint8'))
    decrypted_img.save(output_path)

encrypt_image('input_image.png', 'encrypted_image.png', key=123)
decrypt_image('encrypted_image.png', 'decrypted_image.png', key=123)

Contributing
Feel free to fork this repository, create a branch, and submit a pull request if you have any improvements or additional features to propose.

License
This project is licensed under the MIT License.

