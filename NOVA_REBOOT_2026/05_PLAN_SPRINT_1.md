# 05 — Plan du Sprint 1

## Objectif

Rendre l'ancien projet reproductible avant d'inventer une nouvelle stratégie.

## Progression au 13/09/2026

- [x] Retrouver la base 4 ans, V12/A-D et les scripts P12/E2.
- [x] Contrôler l'intégrité SQLite et calculer les empreintes principales.
- [x] Reproduire V6 P12/E2/portefeuille.
- [x] Reproduire V12 branche D et le chargement des 24 973 courses.
- [ ] Conserver une copie de référence immuable de l'archive.
- [ ] Auditer complètement valeurs, plages, cotes et fuites temporelles.
- [ ] Documenter Python et les dépendances.
- [ ] Figer dataset de référence et futur holdout.
- [ ] Choisir ensuite seulement N1 ou N3.
- [ ] Étudier la collecte légale de cotes horodatées.

Voir [06_AUDIT_ARCHIVE_RECUPEREE.md](06_AUDIT_ARCHIVE_RECUPEREE.md) pour les preuves, empreintes et résultats exacts.

## Arborescence cible

```text
NOVA_REBOOT_2026/
  data/raw/ data/interim/ data/processed/
  configs/ src/ tests/
  experiments/<ID>/
  reports/
```

Les gros fichiers ou données sous licence peuvent rester hors Git. Git conserve alors manifeste, empreintes et instructions de reconstruction, jamais des secrets.

## Critère de passage à une nouvelle expérience

- audit complet produit ;
- données et environnement identifiables ;
- holdout défini avant le test ;
- hypothèse enregistrée selon le protocole.

## Prochaine action

Faire l'audit scientifique complet, puis définir la frontière chronologique du holdout sans regarder ses performances.
