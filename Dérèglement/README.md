# Forensics

# Dérèglement

## Write-UP

Les fichiers **.docx** etc... sont des archives zippés, dézippons les :

> unzip 2021-fcsc-reglement_de_participation.docx -d docs

Cette commande va dézipper le fichier dans un dossier "docs".

Maintenant, naviguons dans le dossier **docs** qui vient d'être créer:

> cd docs

Et **affichons le contenu**:

> ls

Nous pouvons remarquer un dossier **word**, naviguons dedans : 

> cd word

Effectuons un **grep** pour chercher le flag :

> grep -r FCSC{

Nous obtenons le flag : **FCSC{9bc5a6d51022ac}**
