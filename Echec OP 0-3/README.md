# Forensics

# Echec OP 0/3

## Write-UP:

> fdisk fcsc.raw -l

```
Disk fcsc.raw: 10 GiB, 10737418240 bytes, 20971520 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 60DA4A85-6F6F-4043-8A38-0AB83853E6DC
```

Le **Disk Identifier** correspond à notre flag :

Le flag est donc : **FCSC{60DA4A85-6F6F-4043-8A38-0AB83853E6DC}**
