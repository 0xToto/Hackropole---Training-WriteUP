# Babel Web

## Consigne: On vous demande d’auditer ce site en cours de construction à la recherche d’un flag.

### Write-Up:

- En inspectant la page, on remarque un lien commenté (<!-- <a href="?source=1">source</a> -->)
- On modifie afin d'enlever les commentaires et de laisser apparaître le lien
- Si on clique sur ce lien, on voit tout le code PHP ainsi que le code HTML
- On peut remarquer ceci: **@system($_GET['code'])**  ce bout de code nous permettra d’exécuter des commandes système directement en passant des valeurs via la variable GET ‘code’.
- Nous allons donc effectuer une commande PHP afin d'avoir la liste des fichiers PHP présent : **http://localhost:8000/?code=ls**
- Nous voyons 2 fichiers PHP: *flag.php* et *index.php* .
- Ici, le fichier *flag.php* nous intéresse, nous souhaitons voir le contenu: **http://localhost:8000/?code=cat%20flag.php**
- Une page vierge apparait avec le flag en commentaire : ***FCSC{5d969396bb5592634b31d4f0846d945e4befbb8c470b055ef35c0ac090b9b8b7}***
