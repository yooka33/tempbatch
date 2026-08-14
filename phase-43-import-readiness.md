# Phase 43 — Import readiness des classifications externes

> **Décision : BLOCKED**

Généré le 2026-08-14T01:04:08.375Z. Consolidation + validation + dry-run — **aucun import réel, aucun LLM, aucune modification de production**.

## 1. Inventaire des fichiers (source : C:/Users/yooka/Desktop/TAXONOMY)

| Fichier | Taille | Lignes | SHA-256 |
|---|---:|---:|---|
| part-001.jsonl | 16592 | 100 | `203eb184fe665bd678691bfe906d4c208251c92ba4808bef221500ab5d49020d` |
| part-002.txt | 16342 | 100 | `322d0eb07ceec04c884ff6f05f9c7d7d744867bb0b4404155eaa22de9ff63d6b` |
| part-003.jsonl | 16850 | 100 | `1326d545a8e9935defb5051506cf74409f3370b23a8a90b952b13d837f3f901f` |
| part-004.jsonl | 16613 | 100 | `95d63b5654ccd18544adaedcd469458a02b98e822d48e4a81bbf67917d60a11f` |
| part-005.jsonl | 16774 | 100 | `33effa1e56f59777800fb515a0961f0234cc9755feef3100732aa3b603329255` |

Fichiers de classification : **5** · lignes totales : **500**.

## 2–5. Correspondance corpus ↔ classifications

```json
{
  "corpus_total": 500,
  "classified_total": 500,
  "missing": 1,
  "extra": 1,
  "duplicates": 0,
  "entityType_mismatches": 1,
  "parseErrors": 0
}
```

Manquants (extrait) : venue:havre-familial-avec-piscine-deux-pas-du-mans

Supplémentaires (extrait) : venue:havre-familial-avec-piscine-deux-pas-du-mans

## 6–8. Validation taxonomie + contrat Phase 37 + rattachement (validateSeed)

- **Abstentions** (source `categories: []`) : **81** — valides, non importées (jamais une erreur).
- Non-abstentions validées : **419** → acceptées **392** · rejetées **27**.
- Rejets par raison : `{"json-invalid":0,"unknown-entity":1,"duplicate":0,"version-mismatch":0,"invalid-analysis":26}`

### ⛔ IDs de catégorie inconnus de la taxonomie v2026.2 (11) — inventés/incorrects, jamais corrigés automatiquement :
- `food.tapas`
- `hotel.fitness`
- `place.boat-trip`
- `place.festival`
- `place.hotel`
- `place.market`
- `place.music`
- `place.sport.diving`
- `place.sport.fitness`
- `place.sport.golf`
- `place.sport.martial-arts`

### Classifications rejetées (27) — entityId · entityType · categories fournies · raison :
- `venue:venue:practice-67` · cats=`["place.sport.golf"]` · invalid-analysis — aucune catégorie connue de la taxonomie après filtrage des catégories inconnues — jamais un succès à 0 catégorie retenue
- `venue:venue:croisi-re-aux-lueurs-du-soir-d-tours-en-loire` · cats=`["place.boat-trip"]` · invalid-analysis — aucune catégorie connue de la taxonomie après filtrage des catégories inconnues — jamais un succès à 0 catégorie retenue
- `venue:venue:salle-de-cardiotraining-8` · cats=`["place.sport.fitness"]` · invalid-analysis — aucune catégorie connue de la taxonomie après filtrage des catégories inconnues — jamais un succès à 0 catégorie retenue
- `venue:venue:h-tel-de-la-place-des-alpes` · cats=`["place.hotel"]` · invalid-analysis — aucune catégorie connue de la taxonomie après filtrage des catégories inconnues — jamais un succès à 0 catégorie retenue
- `venue:venue:caravane-des-cin-mas-d-afrique` · cats=`["place.festival"]` · invalid-analysis — aucune catégorie connue de la taxonomie après filtrage des catégories inconnues — jamais un succès à 0 catégorie retenue
- `venue:venue:chambray-en-mai` · cats=`["place.festival"]` · invalid-analysis — aucune catégorie connue de la taxonomie après filtrage des catégories inconnues — jamais un succès à 0 catégorie retenue
- `venue:venue:d-couverte-de-l-orgue-porte-ouverte` · cats=`["place.music"]` · invalid-analysis — aucune catégorie connue de la taxonomie après filtrage des catégories inconnues — jamais un succès à 0 catégorie retenue
- `venue:venue:le-maudit-festival` · cats=`["place.festival"]` · invalid-analysis — aucune catégorie connue de la taxonomie après filtrage des catégories inconnues — jamais un succès à 0 catégorie retenue
- `venue:venue:ose-ce-court` · cats=`["place.festival"]` · invalid-analysis — aucune catégorie connue de la taxonomie après filtrage des catégories inconnues — jamais un succès à 0 catégorie retenue
- `venue:venue:site-de-plongee-la-pomme-de-pin` · cats=`["place.sport.diving"]` · invalid-analysis — aucune catégorie connue de la taxonomie après filtrage des catégories inconnues — jamais un succès à 0 catégorie retenue
- `venue:venue:les-mouillotins` · cats=`["place.festival"]` · invalid-analysis — aucune catégorie connue de la taxonomie après filtrage des catégories inconnues — jamais un succès à 0 catégorie retenue
- `venue:venue:sully-h-tel` · cats=`["place.hotel"]` · invalid-analysis — aucune catégorie connue de la taxonomie après filtrage des catégories inconnues — jamais un succès à 0 catégorie retenue
- `venue:venue:festival-cantica-sacra-rocamadour` · cats=`["place.festival"]` · invalid-analysis — aucune catégorie connue de la taxonomie après filtrage des catégories inconnues — jamais un succès à 0 catégorie retenue
- `venue:venue:war-on-screen` · cats=`["place.festival"]` · invalid-analysis — aucune catégorie connue de la taxonomie après filtrage des catégories inconnues — jamais un succès à 0 catégorie retenue
- `venue:venue:march-du-puy-notre-dame` · cats=`["place.market"]` · invalid-analysis — aucune catégorie connue de la taxonomie après filtrage des catégories inconnues — jamais un succès à 0 catégorie retenue
- `venue:venue:jeux-d-orgue` · cats=`["place.festival"]` · invalid-analysis — aucune catégorie connue de la taxonomie après filtrage des catégories inconnues — jamais un succès à 0 catégorie retenue
- `restaurant:venue:mindje-e-care-t` · cats=`["food.tapas"]` · invalid-analysis — aucune catégorie connue de la taxonomie après filtrage des catégories inconnues — jamais un succès à 0 catégorie retenue
- `venue:venue:festival-international-de-la-calligraphie` · cats=`["place.festival"]` · invalid-analysis — aucune catégorie connue de la taxonomie après filtrage des catégories inconnues — jamais un succès à 0 catégorie retenue
- `venue:venue:cluny-danse` · cats=`["place.festival"]` · invalid-analysis — aucune catégorie connue de la taxonomie après filtrage des catégories inconnues — jamais un succès à 0 catégorie retenue
- `venue:venue:h-tel-le-r-gent` · cats=`["place.hotel"]` · invalid-analysis — aucune catégorie connue de la taxonomie après filtrage des catégories inconnues — jamais un succès à 0 catégorie retenue
- `venue:venue:les-rencontres-de-th-tre-amateur` · cats=`["place.festival"]` · invalid-analysis — aucune catégorie connue de la taxonomie après filtrage des catégories inconnues — jamais un succès à 0 catégorie retenue
- `venue:venue:golf-de-chevannes-mennecy-4` · cats=`["place.sport.golf"]` · invalid-analysis — aucune catégorie connue de la taxonomie après filtrage des catégories inconnues — jamais un succès à 0 catégorie retenue
- `hotel:venue:havre-familial-avec-piscine-deux-pas-du-mans` · cats=`["hotel.family"]` · unknown-entity — entityId/entityType absent de l'export — impossible à rattacher au catalogue
- `venue:venue:salle-de-fitness-11` · cats=`["place.sport.fitness"]` · invalid-analysis — aucune catégorie connue de la taxonomie après filtrage des catégories inconnues — jamais un succès à 0 catégorie retenue
- `venue:venue:salle-de-musculation-reserve-au-personnel` · cats=`["place.sport.fitness"]` · invalid-analysis — aucune catégorie connue de la taxonomie après filtrage des catégories inconnues — jamais un succès à 0 catégorie retenue
- `venue:venue:dojo-642` · cats=`["place.sport.martial-arts"]` · invalid-analysis — aucune catégorie connue de la taxonomie après filtrage des catégories inconnues — jamais un succès à 0 catégorie retenue
- `restaurant:venue:la-casita-del-barrio` · cats=`["food.tapas"]` · invalid-analysis — aucune catégorie connue de la taxonomie après filtrage des catégories inconnues — jamais un succès à 0 catégorie retenue

> Autorité taxonomique : `validateAnalysisResult` (taxonomie du code v2026.2 = `taxonomy-reference.json`). contentHash/versions rattachés via l'export `batch-0001.input.jsonl`. **Aucune classification corrigée** (règle de non-modification).

## 9. Statistiques de classification

```json
{
  "abstentions": 81,
  "classifiedWithCategories": 419,
  "avgCategoriesOverClassified": 1.16,
  "byEntityType": {
    "venue": 428,
    "hotel": 60,
    "restaurant": 12
  },
  "confidenceDistribution": {
    "<0.5": 0,
    "0.5-0.79": 2,
    "0.8-0.94": 25,
    "0.95-1": 473
  },
  "withAttributes": 98,
  "attributeDistribution": {
    "outdoor": 97,
    "family": 2,
    "freeEntry": 1
  },
  "topCategories": [
    [
      "place.heritage",
      112
    ],
    [
      "place.sport",
      80
    ],
    [
      "hotel.family",
      32
    ],
    [
      "place.religious-site",
      29
    ],
    [
      "place.library",
      23
    ],
    [
      "place.hiking",
      22
    ],
    [
      "hotel.nature",
      18
    ],
    [
      "place.nature",
      17
    ],
    [
      "place.monument",
      16
    ],
    [
      "place.park",
      11
    ],
    [
      "place.festival",
      11
    ],
    [
      "place.sport.gymnasium",
      10
    ],
    [
      "place.industrial-heritage",
      9
    ],
    [
      "place.multipurpose-hall",
      8
    ],
    [
      "place.castle",
      6
    ],
    [
      "hotel.spa",
      6
    ],
    [
      "place.sport.equestrian-center",
      5
    ],
    [
      "place.garden",
      5
    ],
    [
      "place.performance-hall",
      4
    ],
    [
      "place.museum",
      4
    ]
  ]
}
```

## 10. État de semantic-enrichment.sqlite (copie lecture seule)

```json
{
  "ANALYZED": 28091,
  "ANALYZING": 1,
  "FAILED": 1342,
  "PENDING_jobs": 402,
  "ollamaAnalyzed": 28091,
  "externalAnalyzed": 0
}
```
> Protection Phase 37 : `replaceLocalOllama = false` (défaut). Les 28091 analyses Ollama (ANALYZED locales) ne sont jamais écrasées.

## 11–12. Dry-run d'import (copie isolée, prod intacte)

```json
{
  "executed": false,
  "note": "non exécuté — validations préalables en échec (Étape 5/6 : STOP avant dry-run)"
}
```

## 18. Risques éventuels

- ⛔ 1 entité(s) manquante(s) (ex. venue:havre-familial-avec-piscine-deux-pas-du-mans)
- ⛔ 1 entité(s) supplémentaire(s) (ex. venue:havre-familial-avec-piscine-deux-pas-du-mans)
- ⛔ 1 mismatch(es) entityType (ex. [{"entityId":"venue:havre-familial-avec-piscine-deux-pas-du-mans","classified":"hotel","corpus":"venue"}])
- ⛔ 11 ID(s) de catégorie inconnu(s) de la taxonomie v2026.2 : food.tapas, hotel.fitness, place.boat-trip, place.festival, place.hotel, place.market, place.music, place.sport.diving, place.sport.fitness, place.sport.golf, place.sport.martial-arts
- ⛔ 27 classification(s) non-abstention rejetée(s) : {"json-invalid":0,"unknown-entity":1,"duplicate":0,"version-mismatch":0,"invalid-analysis":26}

## 19. Décision finale

## BLOCKED

Import bloqué — corriger les problèmes ci-dessus avant tout import réel.
