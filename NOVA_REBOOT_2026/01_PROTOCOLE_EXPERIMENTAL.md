# 01 — Protocole expérimental

## Avant chaque test

1. Attribuer un ID unique.
2. Écrire le mécanisme supposé en une phrase.
3. Figer population, variables, pari, mise, seuils et métrique principale.
4. Déclarer quelles données ont servi à inventer l'idée.
5. Interdire toute modification silencieuse après lecture du résultat.

## Validation obligatoire

- séparation strictement chronologique ;
- période finale gelée et jamais utilisée pour régler les paramètres ;
- walk-forward sur plusieurs folds ;
- comparaison à des baselines simples ;
- ROI net selon les rapports réellement disponibles ;
- nombre de paris, hit rate, P&L et drawdown maximal ;
- incertitude par bootstrap groupé par course ou journée ;
- sensibilité aux seuils voisins ;
- ventilation par année, hippodrome, départ, peloton et cote ;
- prudence explicite face aux tests multiples ;
- revue contradictoire cherchant fuite, biais et surapprentissage.

## Statuts autorisés

- **Rejetée** : pertes nettes ou dépendance forte à un segment/fold.
- **À approfondir** : cohérence possible, preuve insuffisante.
- **Candidate live** : survit au holdout, coûts, sensibilité et audit de fuite.
- **Validée** : survit aussi à un test prospectif papier préenregistré.

« Validée » ne signifie jamais gain garanti.

## Reproductibilité

Chaque expérience doit archiver : hypothèse, configuration, commit du code, empreinte SHA-256 des données, sortie machine, rapport et décision. Aucun pari réel pendant la recherche.
