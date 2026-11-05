# Politique de review — proposition V0.1

## Contrat

**Auteur :** comprend la modification, explique le périmètre, indique les vérifications réellement réalisées et rend visibles les risques.

**Agent :** détecte incohérences et angles morts, classe les observations et explicite son incertitude.

**Reviewer :** effectue un examen proportionné au risque ; approuve, demande une correction ou sollicite un arbitrage. Son approbation n'est pas une garantie d'absence de tout défaut.

## Classification

| Type | Exemple | Conséquence |
| --- | --- | --- |
| Défaut démontré | Cas métier incorrect, régression vérifiée | Correction requise |
| Risque significatif non maîtrisé | Doute sur permissions ou données | Clarification, vérification ou arbitrage requis |
| Violation d'une règle établie | Contrôle CI obligatoire échoué | Correction ou exception explicite |
| Préparation insuffisante | Aucune vérification décrite, changement incompréhensible | Compléter avant review |
| Amélioration | Simplification intéressante, non essentielle | Suggestion non bloquante |
| Préférence | Style alternatif sans bénéfice démontré | Non bloquant |

## Merge blockers : progression

**Étape 1 — observation :** signaler l'absence de description utile, d'éléments de vérification, de contexte fonctionnel et les échecs de CI ; mesurer la fréquence et les faux positifs.

**Étape 2 — règles déterministes :** rendre bloquants uniquement les contrôles objectifs **adoptés par l'équipe** (p. ex. CI obligatoire rouge, sections minimales absentes). Un texte rempli automatiquement n'est pas une preuve de compréhension.

**Étape 3 — revue des risques :** l'agent suggère les blocages techniques mais un humain statue sur les cas incertains, avec escalade si nécessaire.

## Désaccords

Tout commentaire bloquant doit reposer sur un fait observable, un risque explicité ou une règle partagée. En cas de désaccord, examiner la preuve, pas le prestige du reviewer ni la réponse d'un LLM. Si le risque ne peut pas être résolu, demander un arbitrage identifié et tracer la décision.

## Limites

La review ne remplace ni la définition du besoin, ni les tests de l'auteur, ni les contrôles automatiques. Les travaux exploratoires peuvent passer par une MR brouillon ; les exceptions urgentes doivent être explicitement assumées.
