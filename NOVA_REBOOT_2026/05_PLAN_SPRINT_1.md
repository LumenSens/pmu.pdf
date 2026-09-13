# 05 — Plan du Sprint 1

## Objectif

Rendre l'ancien projet reproductible avant d'inventer une nouvelle stratégie.

## Ordre strict

1. Retrouver la base 4 ans, les scripts V12/A-D et leurs sorties.
2. Copier ces actifs dans une zone d'import sans modifier les originaux.
3. Calculer leurs empreintes et documenter source, période et schéma.
4. Exécuter l'audit de données.
5. Reproduire au moins un ancien résultat de bout en bout.
6. Si impossible, le déclarer officiellement non reproductible et expliquer pourquoi.
7. Figer le dataset de référence et le futur holdout.
8. Choisir ensuite une première hypothèse N1 ou N3.
9. Étudier en parallèle la collecte légale de cotes horodatées.

## Arborescence cible

```text
NOVA_REBOOT_2026/
  data/raw/ data/interim/ data/processed/
  configs/ src/ tests/
  experiments/<ID>/
  reports/
```

Les gros fichiers ou données sous licence peuvent rester hors Git ; Git conserve alors manifeste, empreintes et instructions de reconstruction, jamais des secrets.

## Critère de passage

Le Sprint 1 ne lance une nouvelle expérience que lorsque :

- la base source est retrouvée et identifiable ;
- l'audit produit un rapport ;
- un résultat ancien est reproduit ou déclaré non reproductible ;
- le holdout futur est défini avant tout nouveau test ;
- le registre est opérationnel.

## Première action demandée à Mathieu

Localiser sur le PC Windows le dossier contenant le CSV/parquet des 24 973 courses et les scripts nommés autour de V12, branche A/B/C/D, P12 ou E2, sans renommer ni éditer les fichiers.
