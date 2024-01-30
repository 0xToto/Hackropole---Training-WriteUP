# Clair Connu

## Consigne: Votre but est de déchiffrer le flag.

### Mis à notre disposition :
- Programme python (clair-connu.py)
- Fichier txt (output.txt)

### Utilité du matériel mis à notre disposition:

- Programme Python: Sert à nous apprendre comment chiffrer des données avec l'opération XOR
- Fichier output.txt: Contient une chaine de caractères.

### Write-Up:

> Déchiffrons le contenu de notre fichier output.txt

Ajoutons un moyen de déchiffrer le contenu:

```
from Crypto.Util.strxor import strxor
flag = bytes.fromhex(open("output.txt", "rb").read().decode())
c = strxor(flag[:4], b"FCSC")
key = c * 20
c = strxor(flag, key[: len(flag)])
print(c)
```
Une fois le programme éxécuté nous obtenons : **b'FCSC{3ebfb1b880d802cb96be0bb256f4239c27971310cdfd1842083fbe16b3a2dcf7}'**
