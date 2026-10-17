# Vérifier un téléchargement

1. Téléchargez l'installateur depuis la page **Releases** de ce dépôt.
2. Calculez son empreinte : `Get-FileHash .\StructureArc_1.2.1_x64-setup.exe -Algorithm SHA256`.
3. Comparez avec `versions/v1.2.1/SHA256SUMS.txt` **et** `releases.json` : elles doivent être identiques.
4. Signature Windows : `Get-AuthenticodeSignature .\StructureArc_1.2.1_x64-setup.exe`. Tant que l'état est `NotSigned`, Windows affichera un avertissement d'éditeur inconnu : seule l'empreinte SHA-256 prouve l'intégrité du fichier.

Les rapports de preuves (`versions/*/preuves`) ont le nom de machine, le nom d'utilisateur et les chemins locaux remplacés ; les originaux sont conservés par le propriétaire.
