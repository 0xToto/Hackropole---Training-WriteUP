# Hardware

# File Format

## Write-Up

Programme python permettant d'ouvrir le fichier, et d'afficher le flag :

```
import numpy as np
import hashlib
with open('file-format.iq', 'rb') as f:
    data = np.fromfile(f, dtype=np.float32)
    i_components = data[::2]  # Composantes I
    q_components = data[1::2]
    concatenated_data = np.concatenate((i_components, q_components))
    byte_data = concatenated_data.tobytes()
    hash_object = hashlib.sha256(byte_data)
    hex_dig = hash_object.hexdigest()
    print(f'FCSC{{{hex_dig}}}')
```

Le flag est donc : **FCSC{843161934a8e53da8723047bed55e604e725160b868abb74612e243af94345d7}**
