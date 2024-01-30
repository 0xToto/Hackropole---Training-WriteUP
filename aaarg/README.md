# AAARG

## Consigne: Vous devez afficher le flag, quelque soit le moyen utilisé !

### Pré-Analyse:

> file aaarg.txt -> afin de connaitre le type de fichier que nous avons ici (ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 3.2.0, BuildID[sha1]=f5b07c01242cc5987bed7730c2762ae0491b5ddc, stripped)

aaarg est donc un fichier **exécutable ELF x86-64, strippé**

Afin de trouver le flag, nous allons utiliser le tool _**Ghidra**_ disponible sur github !

On trouve donc:
**FCSC{f9a38adace9dda3a9ae53e7aec180c5a73dbb7c364fe137fc6721d7997c54e8d}**
