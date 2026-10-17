# Vérifier un téléchargement

Les installateurs publiés ici sont **signés** (signature Windows Authenticode, certificat Certum, horodatée). Vérifiez toujours deux choses :

1. **La signature** : `Get-AuthenticodeSignature .\StructureArc_X.Y.Z_x64-setup.exe` doit afficher `Status : Valid`. Un fichier dont l'état n'est pas `Valid` ne vient pas de nous : ne l'exécutez pas. (Sur l'explorateur : clic droit → Propriétés → Signatures numériques.)
2. **L'empreinte SHA-256** : `Get-FileHash .\StructureArc_X.Y.Z_x64-setup.exe -Algorithm SHA256`, à comparer avec `versions/vX.Y.Z/SHA256SUMS.txt` **et** `releases.json` : elles doivent être identiques.

Les installateurs ont été signés après leur fabrication : l'empreinte du fichier signé est celle publiée ici (elle peut différer de l'empreinte d'origine citée dans d'anciennes notes).
