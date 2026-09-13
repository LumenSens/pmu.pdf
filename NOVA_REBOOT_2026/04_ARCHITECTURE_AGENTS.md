# 04 — Architecture des agents

## Responsabilités

- **Mathieu — propriétaire** : objectifs, budget, tolérance au risque, décision finale.
- **ChatGPT — chef de protocole** : source de vérité, spécifications, code, tests, synthèse et arbitrage.
- **Grok — chercheur divergent** : recherche externe, idées atypiques, contre-hypothèses.
- **Agent Data** : provenance, qualité, dictionnaire et fuites.
- **Agent Expérimentation** : implémentation reproductible et rapports.
- **Agent Sceptique** : tente de casser chaque résultat.

## Flux de travail

1. Une idée est inscrite dans le registre.
2. Le chef de protocole la transforme en test figé.
3. Data confirme que les variables existaient avant le départ.
4. Expérimentation exécute le test chronologique.
5. Sceptique cherche biais, fuite et fragilité.
6. ChatGPT classe : rejetée, à approfondir ou candidate live.
7. Mathieu autorise ou refuse l'étape suivante.

## Garde-fous

- aucun agent ne peut déclarer seul une stratégie rentable ;
- aucune discussion ne remplace une sortie reproductible ;
- Grok propose, mais ses idées suivent exactement le même protocole ;
- les agents ne réoptimisent pas les seuils après coup sans créer une nouvelle version d'hypothèse ;
- les désaccords sont documentés, pas lissés.
