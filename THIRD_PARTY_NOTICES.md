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

Aucun code tiers n'a été copié dans le dépôt.
