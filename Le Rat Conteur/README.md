# Cryptography

## Le Rat Conteur

### Déchiffrage grâce à un programme python: 

```
from cryptography.hazmat.backends import default_backend
from cryptography.hazmat.primitives.ciphers import Cipher, algorithms, modes
from Crypto.Util.Padding import unpad
import binascii

key = binascii.unhexlify("00112233445566778899aabbccddeeff")

iv = b'\x00' * 16

with open('flag.jpg.enc', 'rb') as file:
    ciphertext = file.read()

cipher = Cipher(algorithms.AES(key), modes.CTR(iv), backend=default_backend())

decryptor = cipher.decryptor()

plaintext = decryptor.update(ciphertext) + decryptor.finalize()

with open('image_dechiffree.jpg', 'wb') as file:
    file.write(plaintext)

print("Déchiffrement terminé avec succès.")
```

> Ce programme me permet de me renvoyer l'image au format jpg, laissant apparaitre le flag: FCSC{879C2FEE3B9EFBC651050F881841D209}
