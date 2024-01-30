# Cryptography

# ROT13

## Déchiffrage grâce à un programme python:

```
def decrypt_rot13(text):
    result = ""
    for char in text:
        if 'a' <= char <= 'z':
            result += chr((ord(char) - ord('a') - 13) % 26 + ord('a'))
        elif 'A' <= char <= 'Z':
            result += chr((ord(char) - ord('A') - 13) % 26 + ord('A'))
        else:
            result += char
    return result

encrypted_text = """GBQB yvfgr :
- Cnva (2 onthrggrf)
- Ynvg (1 yvger)
- Pbevnaqer (fhegbhg cnf, p'rfg cnf oba)
- 4 onanarf, 4 cbzzrf, 4 benatrf
- Cbhyrg (4 svyrgf qr cbhyrg)
- 1 synt : SPFP{rq24p7sq86p2s0515366}
- Câgrf (1xt)
- Evm (fnp qr 18xt)
- Abheve zba qvabfnher"""
decrypted_text = decrypt_rot13(encrypted_text)

print(f"Texte chiffré : {encrypted_text}")
print(f"Texte déchiffré : {decrypted_text}")
```

Texte **avant** chiffrage:
> GBQB yvfgr :
> Cnva (2 onthrggrf)
> Ynvg (1 yvger)
> Pbevnaqer (fhegbhg cnf, p'rfg cnf oba)
> 4 onanarf, 4 cbzzrf, 4 benatrf
> Cbhyrg (4 svyrgf qr cbhyrg)
> 1 synt : SPFP{rq24p7sq86p2s0515366}
> Câgrf (1xt)
> Evm (fnp qr 18xt)
> Abheve zba qvabfnher

Texte **après** chiffrage:
> Pain (2 baguettes)
> Lait (1 litre)
> Coriandre (surtout pas, c'est pas bon)
> 4 bananes, 4 pommes, 4 oranges
> Poulet (4 filets de poulet)
> 1 flag : FCSC{ed24c7fd86c2f0515366}
> Pâtes (1kg)
> Riz (sac de 18kg)
> Nourir mon dinosaure

Le flag est donc : **FCSC{ed24c7fd86c2f0515366}**
