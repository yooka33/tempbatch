# Corpus batch-001 — découpage en parties de 100 entités

Découpage **physique** du corpus de classification externe en 5 fichiers de 100 entités, assez
petits pour être lus intégralement par une IA externe (ChatGPT) sans troncature.

> **Découpage octet-pour-octet uniquement.** Aucune classification, aucun appel LLM/Ollama, aucun
> import, aucune modification de contenu / champs / ordre / `entityId` / `entityType` / taxonomie /
> catalogue / `semantic-enrichment.sqlite` / scheduler / moteur. Chaque ligne du corpus source est
> copiée telle quelle dans exactement un fichier de sortie, dans l'ordre original.

## Fichier source

`../corpus-batch-001.jsonl` — **500 entités** (JSONL, 1 objet par ligne, LF, un seul `\n` final).
SHA-256 : `9a816959f36ed76874e92b9a6d652f6d997c962baeee62ffe08b778241581bd7`.

## Les 5 parties (répartition 100 / 100 / 100 / 100 / 100)

| Fichier | Lignes source | Entités | SHA-256 |
|---|---|---:|---|
| `part-001.jsonl` | 1–100 | 100 | `fa1e91a6dae1fb9ea70400120cd2ede76a4dc1c8a5701b08e18c027c2eae8dfd` |
| `part-002.jsonl` | 101–200 | 100 | `6a5021f68510fc92dbb61674a2f7fef0ac66eda907e998a2b6c353399e323a84` |
| `part-003.jsonl` | 201–300 | 100 | `61058b649994bf0788a89ce67a52b9221c6cdfa748d43f21dcd5f865dc5692eb` |
| `part-004.jsonl` | 301–400 | 100 | `656f1e1fa922052699fca5716e032d3c73b1e56250f5902db3c988573691235d` |
| `part-005.jsonl` | 401–500 | 100 | `f94edd371f620e8cde912101b14c926516d8fb38eec92c6eb3ada4eb1bdb0627` |

Reconstruction (concaténation `part-001 → part-005`) :
SHA-256 = `9a816959f36ed76874e92b9a6d652f6d997c962baeee62ffe08b778241581bd7`
→ **identique au SHA-256 du corpus source** (`reconstructionMatchesSource = true`).

## Vérifications effectuées (réelles, exécutées)

Par le script (`splitExternalCorpus.ts`) — **10/10 OK** :

1. les 5 fichiers existent ;
2. chaque fichier contient exactement 100 objets JSON ;
3. le corpus source contient exactement 500 objets JSON ;
4. le total des parties est exactement 500 ;
5. les `entityId` source == parties (même ensemble) ;
6. aucun `entityId` perdu ;
7. aucun `entityId` dupliqué entre les parties ;
8. l'ordre des `entityId` concaténés depuis les 5 parties == ordre du corpus source ;
9. le contenu JSON de chaque ligne == source (comparaison **octet pour octet** des records) ;
10. SHA-256 reconstruit (`part-001→005`) == SHA-256 source.

Contre-vérification **indépendante** (hors script) :
- `cat part-001.jsonl … part-005.jsonl | sha256sum` = `9a816959…81bd7` = SHA-256 source ;
- `wc -l` : 100 / 100 / 100 / 100 / 100 (500) ;
- parse JSON indépendant : 100 objets valides par partie, 500 au total, 500 `entityId` uniques,
  ordre identique à la source.

## Déterminisme

Le découpage est une fonction pure des octets du source : une **seconde exécution** produit des
fichiers identiques (mêmes SHA-256, vérifié). Le script ne modifie jamais `corpus-batch-001.jsonl`.

## Reproduction

```bash
pnpm --filter=@radius/api exec tsx scripts/validation/phase43/splitExternalCorpus.ts
```

## Aucune classification / aucun import

Cette étape est **strictement** un découpage. Aucune entité n'a été classifiée, aucun LLM n'a été
appelé, aucun import sémantique n'a été effectué, aucun composant métier n'a été modifié.
Manifeste machine : `manifest.json`.
