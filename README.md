# Agent Factory

Référentiel léger pour concevoir, faire évoluer et évaluer des assistants IA de développement logiciel.

**Statut :** V0.1 — fondations. Les prompts proposés sont des **bases de travail**, pas des remplacements automatiques des agents existants.

## Objectifs

- Des changements **fonctionnellement vérifiables** et des risques maîtrisés.
- Un code **suffisamment simple, maintenable et sûr**, sans recherche de perfection subjective.
- Une responsabilité claire : l'auteur prépare et comprend son travail ; l'agent aide à vérifier ; le reviewer décide.
- Une documentation **courte et utile**, plutôt qu'une accumulation de texte généré.

## Organisation

```text
principles/   Règles d'ingénierie et d'usage de l'IA
prompts/      Bases à adapter aux deux agents existants
policies/     Contrat de revue et motifs de blocage
templates/    Tickets Jira et descriptions de MR concis
```

## Workflow cible

1. **Jira** : besoin et critères d'acceptation assez clairs pour être vérifiés ; sinon, clarifier avec la personne responsable.
2. **Développement** : l'auteur pilote l'IA, relit le code et réalise des vérifications pertinentes.
3. **Préparation MR** : description concise, preuves de tests et risques résiduels.
4. **Review readiness** : détecter les éléments manquants avant la review approfondie.
5. **Review technique** : confronter besoin, explication de l'auteur et code ; classer les remarques.
6. **Décision humaine** : approuver, demander des corrections ou arbitrer le risque.

## Démarrage

- Comparer `prompts/` aux instructions actuelles des agents avant tout changement.
- Expérimenter les règles en **mode observation** avant de configurer des merge blockers automatiques.
- Mesurer la qualité des tickets, les retours pour préparation insuffisante et les discussions subjectives.
- Ajuster les règles à partir de cas réels ; ne créer un nouvel agent que si le besoin est démontré.

## Confidentialité

Ne pas déposer ici de code client, secrets, tickets internes, extraits de MR, configurations privées ou instructions d'agents appartenant à une organisation sans autorisation. La confidentialité du dépôt ne remplace pas cette vérification.
