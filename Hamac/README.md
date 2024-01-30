# Cryptography

## Write-Up:

#### Crackage du mot de passe grâce à hashcat et rockyou:
> hashcat -m 1450 -a 0 "951bd9d2caae0d9e9a5665b4fc112809aac9f5f9ecbcfc5ad8e23cb1d020201d:FCSC2022" rockyou.txt -> omgh4xx0r
### Déchiffrage du mot de passe grâce à un programme python:

```
from Crypto.Cipher import AES
from Crypto.Hash import SHA256
from Crypto.Util.Padding import unpad

iv = bytes.fromhex("ea425b2ea4bb67445abe967e3bd1b583")
hash = bytes.fromhex("69771c85e2362a35eb0157497e9e2d17858bf11492e003c4aa8ce1b76d8d3a31ccc3412ec6e619e7996190d8693299fc3873e1e6a96bcc1fe67abdf5175c753c09128fd1eb2f2f15bd07b12c5bfc2933")
password = "omgh4xx0r"

key = SHA256.new(password.encode()).digest()
cipher = AES.new(key, AES.MODE_CBC, iv=iv)
plain = unpad(cipher.decrypt(hash), AES.block_size)
print(plain)
```
Résultat: **FCSC{5bb0780f8af31f69b4eccf18870f493628f135045add3036f35a4e3a423976d6}**
