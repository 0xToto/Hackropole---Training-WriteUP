# Cryptography

## La PIN

Après analyse du fichier python mis à notre disposition (lapin.py) nous nous rendons compte qu'il suffirait de trouver le code PIN à 4 chiffres pour obtenir le Flag:

Ainsi, voici un programme python permettant de *bruteforce* le PIN : 

```from Crypto.Cipher import AES
from Crypto.Protocol.KDF import scrypt
from Crypto.Util.number import long_to_bytes

with open("output (2).txt", "rb") as f:
    hex_output= bytes.fromhex(f.readline().decode("utf-8")) #Attention à bien convertir notre output en bytes !
    nonce = hex_output[:16] # 16 bytes de nonce
    c= hex_output[16:-16]
    tag = hex_output[-16:] # 16 bytes de tag
    for i in range(1,10000):
        print("Pin: ",i)
        pin = i
        k = scrypt(long_to_bytes(pin), b"FCSC", 32, N = 2 ** 10, r = 8, p = 1)
        aes = AES.new(k, AES.MODE_GCM, nonce=nonce) # N'oublions pas le nonce ici !
        flag = aes.decrypt(c)
        if b"FCSC" in flag:
            print(flag)
            break
```
Le programme s'arrête à **6273** et nous donne le flag : **FCSC{c1feab88e6c6932c57fbaf0c1ff6c32e51f07ae87197fcd08956be4408b2c802}**
