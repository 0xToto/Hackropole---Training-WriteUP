# Cap ou Pas Cap

## Consigne: Voici la capture d’une communication réseau entre deux postes. Un fichier a été échangé et vous devez le retrouver. Le flag est présent dans le contenu du fichier.

### Write-Up:

**Vérifions le type de fichier de cap.pcap**
> *file cap.pcap* -> pcap capture file, microsecond ts (little-endian) - version 2.4 (Ethernet, capture length 262144)

**Identifions le nombre de session TCP :**
> *tshark -r cap.pcap -T fields -e tcp.stream |sort -n|uniq* -> 0  1
Il y a donc **deux** sessions TCP

**Affichons le payload:**
> *tshark -q -nr cap.pcap -z follow,tcp,ascii,0* -> Le fichier **flag.zip** a transité vers 172.20.20.133:20200. Il a été préalablement converti en hexdump avec la commande xxd.

 **Trouvons le payload hexdump du transfert de fichier:**
 > *tshark -q -nr cap.pcap -z follow tcp,ascii,1*

**Affichons le contenu du .zip à l'aide de l'hexdump et de la commande xxd:**
> *tshark -o data.show_as_text:TRUE -r cap.pcap -Y "tcp.dstport == 20200" -T fields -e data.text |xargs |xxd -r -p - |zmore* -> **FCSC{6ec28b4e2b0f1bd9eb88257d650f558afec4e23f3449197b4bfc9d61810811e3}**
