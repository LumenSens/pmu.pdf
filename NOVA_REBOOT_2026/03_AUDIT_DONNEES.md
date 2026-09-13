# 03 — Audit des données

## Confiance provisoire

| Couche | Source évoquée | Confiance | Action |
|---|---|---|---|
| Courses/résultats/partants | Trotstats v4 / Dataturf | Bonne mais non auditée ici | retrouver puis contrôler |
| Cotes finales | historique existant | Moyenne | documenter type et instant |
| Ferrure | ParisTurf/Dataturf | Incomplète | consolider l'historique 2023+ |
| Type de départ | base + tableur autostart | Moyenne | comparer à une source officielle |
| Presse | Week-End | Contextuelle | tracer date/heure, éviter les fuites |
| Cotes intraday | Absentes | Nulle | étudier une collecte légale horodatée |

## Contrôles minimaux

- provenance, licence/conditions d'usage et dates de collecte ;
- empreinte SHA-256 de chaque fichier brut ;
- plage de dates et comptage réunions/courses/partants ;
- unicité de la clé course-partant ;
- doublons et valeurs manquantes par colonne ;
- cohérence date-réunion-course, arrivée et non-partants ;
- cotes nulles/impossibles et définition exacte des rapports ;
- contrôles de fuite temporelle ;
- comparaison manuelle d'un échantillon avec une source de référence.

## Données intraday souhaitées

Si faisable légalement et techniquement : capturer pour chaque partant les cotes à T-30, T-15, T-10, T-5, T-2 et T-1, avec horodatage UTC, source, statut non-partant et identifiant stable de course.

Aucune donnée transformée ne remplace le brut : les transformations doivent être produites par code.
