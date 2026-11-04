# Notices tierces

**Statut : liste provisoire des dépendances DIRECTES, établie de mémoire des licences publiques habituelles de ces projets. Elle n'a PAS été générée par un outil.** Avant toute distribution, régénérer la liste complète (dépendances transitives incluses) avec `npx license-checker` et `cargo license` / `cargo about`, puis vérifier les textes de licence.

| Composant | Rôle | Licence attendue |
|---|---|---|
| Tauri, tauri-build, tauri-plugin-dialog | shell desktop | MIT ou Apache-2.0 |
| rusqlite (SQLite embarqué, domaine public) | stockage, FTS5 | MIT (SQLite : domaine public) |
| tree-sitter, tree-sitter-typescript, tree-sitter-javascript, tree-sitter-python | analyse syntaxique | MIT |
| ignore (ripgrep) | parcours + .gitignore | MIT ou Unlicense |
| sha2 | empreintes SHA-256 | MIT ou Apache-2.0 |
| serde, serde_json, thiserror, uuid | Rust | MIT ou Apache-2.0 |
| tempfile (dev) | tests Rust | MIT ou Apache-2.0 |
| React, react-dom | UI | MIT |
| Vite, @vitejs/plugin-react, vitest | build/tests | MIT |
| TypeScript | compilation | Apache-2.0 |
| @testing-library/*, jsdom | tests | MIT |

Les composants de reconnaissance vocale ci-dessous sont distribués avec l’installateur à partir de la version 1.3.35. Leurs textes de licence vérifiés sont également inclus dans le dossier vocal installé.


## Reconnaissance vocale locale — 1.3.35

whisper.cpp b5454 (exécutables officiels Windows x64) et les poids Whisper base multilingues sont distribués sous licence MIT. Les poids proviennent de la conversion ggml du modèle OpenAI Whisper. Les empreintes du moteur et du modèle sont vérifiées avant assemblage et à leur chargement.

```text
whisper.cpp
https://raw.githubusercontent.com/ggml-org/whisper.cpp/b5454/LICENSE
MIT License

Copyright (c) 2023-2026 The ggml authors

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.


Whisper model
https://raw.githubusercontent.com/openai/whisper/main/LICENSE
MIT License

Copyright (c) 2022 OpenAI

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

```
