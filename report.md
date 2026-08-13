# Corpus batch-001 — second découpage (50 × 10 entités)

Découpage **physique** de chaque `parts/part-00N.jsonl` (100 entités) en 10 sous-parties de 10
entités, pour lecture intégrale sans troncature par une IA externe (ChatGPT).

> **Découpage octet-pour-octet uniquement.** Aucune classification, aucun LLM, aucun import, aucun
> reformatage. Une ligne source = une ligne cible (verbatim, terminateur inclus), ordre strictement
> préservé. Aucune modification du corpus original / taxonomie / contrat Phase 37 / catalogue /
> `semantic-enrichment.sqlite`.

## Fichiers sources utilisés
`parts/part-001.jsonl … parts/part-005.jsonl` (5 fichiers × 100 = 500 entités), issus du corpus
canonique `corpus-batch-001.jsonl` (SHA-256 `9a816959f36ed76874e92b9a6d652f6d997c962baeee62ffe08b778241581bd7`).

## 50 fichiers créés
`split/part-00N-0M.jsonl` pour N ∈ {001…005}, M ∈ {01…10} — 50 fichiers × **10 lignes** = **500 entités**.
Ordre de concaténation : `part-001-01 → part-001-10 → part-002-01 → … → part-005-10`.

## Résultats (10/10 contrôles, exécutés par script + contre-vérif indépendante)

- **500/500 entités conservées** ; **0 perte** ; **0 doublon** (500 `entityId` uniques).
- **Ordre préservé** : la séquence des `entityId` concaténés == corpus original, à l'identique.
- **JSON valides** : chaque ligne de chaque sous-fichier parse sans erreur.
- **Byte-exact** : chaque record de sous-fichier == record source correspondant (comparaison d'octets).
- Chaque part source = 100 lignes ; chaque sous-partie = 10 lignes ; total 50 sous-parties = 500.

## SHA-256

- **SHA-256 source** (corpus original correspondant à ces 500 lignes) :
  `9a816959f36ed76874e92b9a6d652f6d997c962baeee62ffe08b778241581bd7`
- **SHA-256 reconstruit** (concaténation ordonnée des 50 sous-fichiers) :
  `9a816959f36ed76874e92b9a6d652f6d997c962baeee62ffe08b778241581bd7`
- **Identiques → `reconstructionMatchesCorpusSource = true`.**

Contre-vérification indépendante (hors script) : `cat $(ls part-*-*.jsonl | sort) | sha256sum`
= `9a816959…81bd7` = SHA-256 source ; `wc -l` = 10 par fichier (500 total) ; 50 fichiers.
Déterminisme : seconde exécution identique. Le SHA-256 de chaque sous-fichier est dans `manifest.json`.

## Aucune classification / aucun import
Cette étape est **strictement** un découpage de fichiers. Aucune entité classifiée, aucun LLM
appelé, aucun import, aucun composant métier modifié, corpus original inchangé.
