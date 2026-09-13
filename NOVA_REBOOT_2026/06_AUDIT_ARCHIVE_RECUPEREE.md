# 06 — Audit de l’archive Nova 5 récupérée

Date de contrôle : 13/09/2026  
Archive reçue : `f244b013-373d-48da-947d-918f775b9028.zip`  
Taille décompressée annoncée : 223 135 388 octets, 52 entrées.

## Verdict

**C’est bien l’archive opérationnelle recherchée.**

Elle contient la base SQLite, trois exports CSV, le collecteur, les modèles, les scripts P12/E2, les branches A–D jusqu’à V12 et des rapports historiques.

## Actifs principaux

- `nova5.db` : 194 686 976 octets ;
- `dataset_complet.csv` : 10 597 lignes de données ;
- `dataset_ml.csv` : 9 319 lignes ;
- `dataset_v4.csv` : 23 889 lignes ;
- scripts V6 walk-forward, V7 branche A, V8/V10 branche B, V11 branche C, V12 branche D ;
- rapports V1 à V6 et analyse du fold 3.

## Empreintes SHA-256

| Fichier | SHA-256 |
|---|---|
| `nova5.db` | `acea54a17b8ca4f64cf2a11d53745d004cbf10a87d9cd0a8fa88fb8dc44032bd` |
| `dataset_complet.csv` | `1f32c1bea772fe20c95979a8829b8b1d3e0c8d5b05892a923bf5d98e4b094526` |
| `dataset_ml.csv` | `cf8a294e86fb6c05cd76840e182fcfb587fe3a80e31b70ccb985db1ec1dc3c4c` |
| `dataset_v4.csv` | `34c58c054dc59640334be479f9bdebacd61c04ef3240a275042e34576d036f73` |

## Base SQLite

| Table | Lignes |
|---|---:|
| courses | 31 615 |
| partants | 400 620 |
| collect_log | 2 455 |
| watchlist | 147 |
| bets | 0 |
| predictions | 0 |

Période : **23/03/2022 → 21/03/2026**, 1 428 dates distinctes.

Contrôles réussis :

- `PRAGMA integrity_check = ok` ;
- aucune violation de clé étrangère ;
- aucun partant orphelin ;
- aucun doublon sur `course_id + numero` ;
- aucune date, hippodrome ou taille de peloton manquante dans `courses`.

Points à surveiller :

- la colonne `cote` est entièrement vide ; les scripts utilisent `cote_avant`, présente sur toutes les lignes mais valant parfois 0 et jusqu’à 999 ;
- `rapport_place` est renseigné sur 89 296 partants, positif sur 88 150 ;
- 31 526 courses indiquent la source `api_pmu`, 89 la source `pdf` ;
- les disciplines contiennent deux graphies : `ATTELE` (31 526) et `ATTELÉ` (89) ;
- la qualification « française » dépend d’une fonction de filtrage par hippodrome dans les scripts et doit être auditée séparément.

## Reproduction effectuée

### V12 — branche D

Commande exécutée sans modifier le script :

- 24 973 courses françaises trot attelé chargées ;
- 8 481 courses répondent au filtre sur toute la base ;
- walk-forward évalué sur 4 298 paris ;
- ROI total **−0,1 %**, P&L **−25 €**, 2 folds positifs sur 4 ;
- verdict du script : **B — insuffisant** ;
- baseline tous favoris : ROI **−3,4 %**.

Le script mesure un delta de +3,3 points face à sa baseline, mais n’atteint pas son critère préfixé de ROI ≥ +3 %. Ce résultat ne valide donc pas une stratégie rentable.

### V6 — P12 / E2 / portefeuille

Reproduction directe :

| Stratégie | N | ROI | P&L | Folds positifs | Verdict du script |
|---|---:|---:|---:|---:|---|
| P12 | 248 | −6,6 % | −82,25 € | 1/3 | Rejet |
| E2 | 239 | −1,9 % | −23,25 € | 2/3 | Prometteur, mais fold 3 à −23,1 % |
| Portefeuille | 487 | −4,3 % | −105,50 € | 1/3 | Rejet |

## Conséquence pour le Sprint 1

La condition « retrouver les actifs » est remplie et deux résultats anciens ont été reproduits. Il reste à :

1. conserver l’archive originale sans modification ;
2. produire l’audit complet des valeurs, plages et fuites temporelles ;
3. documenter l’environnement/dépendances ;
4. décider comment référencer la base sans pousser le fichier SQLite de 195 Mo dans GitHub ;
5. définir le futur holdout avant toute nouvelle hypothèse.

**Statut : récupération confirmée ; audit minimal réussi ; audit scientifique complet encore à faire.**
