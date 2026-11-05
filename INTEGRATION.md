# Intégration d'Agent Factory dans notre workflow

> **Document de transmission à mon canal IA de gestion des agents.**
>
> Dépôt de référence : https://github.com/spellier/agent-factory
>
> Statut : cadrage et proposition. **Aucun déploiement automatique n'est demandé.**

## Instructions à mon canal IA

Nous disposons déjà de deux agents utilisés dans un environnement de développement professionnel :

- **Agent Dev** : compréhension du besoin, conception, implémentation et vérifications.
- **Agent MR** : analyse de merge requests et échange avec le reviewer humain sur les observations techniques.

Nous venons de constituer un référentiel versionné **Agent Factory** sur GitHub. Son objectif n'est pas de remplacer aveuglément nos agents, mais d'améliorer progressivement notre façon de travailler.

### Pourquoi ce chantier ?

L'IA peut produire des changements volumineux que leurs auteurs ne comprennent ou ne vérifient pas suffisamment. Le reviewer reçoit alors une charge excessive : reconstituer le besoin, comprendre le code, découvrir les impacts et parfois concevoir les tests manquants.

La situation est aggravée par des tickets Jira parfois trop vagues (par exemple : « Développer la timeline »). Quand le besoin n'est pas spécifié, l'agent de développement risque de décider implicitement du comportement attendu ; la review ne dispose ensuite d'aucune base fiable pour juger la conformité fonctionnelle.

Nous voulons **une chaîne de responsabilité claire**, pas une compétition entre les prompts de l'auteur et du reviewer.

### Principes à respecter

1. **Fonctionnel vérifiable** : un changement doit répondre à des attentes explicites et testables. Les critères inconnus restent inconnus ; l'IA ne doit pas les inventer.
2. **Qualité professionnelle pragmatique** : pas de perfection stylistique, mais une attention réelle à la sécurité, aux données, aux régressions, à la complexité et à la maintenabilité.
3. **Auteur responsable** : il doit comprendre son code, pouvoir l'expliquer, identifier les impacts et attester les vérifications qu'il a réellement effectuées.
4. **Reviewer responsable, mais pas auteur de substitution** : il examine les risques et les preuves disponibles ; il n'a pas à reconstruire entièrement un travail insuffisamment préparé.
5. **Aucun argument d'autorité fondé sur l'IA** : « mon agent l'a dit » ne prouve rien. Les remarques doivent s'appuyer sur des faits, des exigences, des risques ou des règles connues.
6. **Exigences proportionnées au risque** : ne pas appliquer aux changements simples le même formalisme qu'aux modifications critiques.
7. **Documentation minimale utile** : préférer quelques lignes précises à une description de 400 lignes générée automatiquement.

### Workflow cible à étudier

```text
Ticket Jira
  → clarification du besoin et critères d'acceptation
  → développement assisté par IA
  → vérifications et relecture par l'auteur
  → description concise de la MR
  → contrôle de préparation (review readiness)
  → review technique assistée par IA
  → décision humaine : approbation, corrections ou arbitrage
  → merge
```

**Un ticket insuffisant ne doit pas être automatiquement enrichi par des hypothèses présentées comme des exigences confirmées.** Une clarification ciblée avec la personne compétente doit être privilégiée.

### Travaux demandés sur l'agent MR (priorité 1)

Étudier comment enrichir **l'agent existant**, sans perdre ses fonctionnalités actuelles de revue et de dialogue :

- Commencer par un résumé court : **« Voici ce que j'ai compris de la MR »**.
- Confronter **le besoin Jira**, **ce que l'auteur annonce** et **ce que le diff semble réellement modifier**.
- Distinguer les éléments prouvés, les hypothèses et les points non vérifiables avec les données accessibles.
- Détecter les préparations incomplètes : objectif absent, tests non détaillés, impacts non documentés, ticket trop ambigu.
- Classer chaque observation : **défaut démontré**, **risque significatif**, **écart à une règle partagée**, **information manquante**, **amélioration facultative** ou **préférence personnelle**.
- Pour tout blocage proposé, préciser **preuve ou fait observable**, **conséquence**, **référence éventuelle à une règle** et **action attendue**.
- Produire un compte rendu **court**, concentré sur les sujets prioritaires, avec possibilité d'approfondir sur demande.
- Continuer à questionner les jugements du reviewer, plutôt qu'approuver ses intuitions par complaisance.
- Ne jamais approuver ni bloquer automatiquement une MR sur un jugement subjectif du LLM.

Une approbation humaine signifie que les vérifications convenues et les risques identifiés ont été suffisamment examinés ; ce n'est pas une garantie d'absence de bugs.

### Travaux demandés sur l'agent Dev (priorité 2)

Étudier comment lui faire :

- Vérifier, **avant de coder**, que le besoin et les critères d'acceptation sont suffisamment clairs.
- Poser peu de questions, mais les bonnes, lorsqu'un ticket est ambigu.
- Distinguer une proposition de comportement d'une exigence métier confirmée.
- Aider à concevoir les tests pertinents et indiquer honnêtement ceux qui ont réellement été exécutés.
- Préparer une description de MR concise : **quoi/pourquoi**, **choix significatifs**, **vérifications réalisées**, **risques ou limites**.
- Demander à l'auteur de confirmer sa compréhension des changements, sans prétendre l'avoir vérifiée uniquement grâce à une case cochée.

### Merge blockers : attention aux faux remèdes

Ne pas activer immédiatement de nouvelles règles de blocage sur la base d'une appréciation IA.

Proposer d'abord une phase **d'observation**, puis envisager des critères objectivables et approuvés par l'équipe : CI obligatoire en échec, informations réellement indispensables absentes, risque critique non traité, besoin fonctionnel impossible à vérifier, etc.

Une belle description de MR peut être générée automatiquement sans aucune compréhension : sa seule présence n'est **pas** une preuve.

Les désaccords persistants sur un risque important doivent pouvoir être arbitrés par un responsable technique identifié ; les préférences de style non étayées ne doivent pas devenir bloquantes.

### Comment utiliser le dépôt

- `README.md` : vision d'ensemble.
- `principles/` : principes communs.
- `prompts/dev-agent.md` et `prompts/mr-review-agent.md` : **ébauches d'évolution**, pas des versions de production.
- `policies/review-policy.md` : proposition de contrat de review.
- `templates/` : modèles minimaux Jira et MR.

**Ne pas supposer que les agents ont automatiquement accès à ces fichiers.** Si ce dépôt privé n'est pas accessible depuis l'environnement professionnel, signaler cette limite et travailler à partir de copies autorisées ou de textes génériques. Ne pas exposer de secrets, de code client ou d'instructions internes sans autorisation.

## Ce que j'attends maintenant

1. **Examiner d'abord les instructions actuelles** de mes deux agents, si elles sont disponibles dans notre contexte.
2. Comparer leurs fonctionnalités existantes aux idées d'Agent Factory ; **identifier contradictions, redondances et risques de régression**.
3. Proposer une **V0.2 minimale**, prioritairement pour l'agent MR, sous forme d'ajouts ou de modifications ciblées.
4. Expliquer ce qui doit être **bloquant, informatif ou laissé à l'humain**.
5. Proposer **quelques cas de test concrets** : ticket vague, MR bien préparée, code correct mais complexe, vrai défaut fonctionnel, désaccord purement stylistique.
6. **Attendre ma validation avant toute modification ou déploiement** des agents de production.
7. Après validation, versionner la proposition dans Agent Factory si l'accès et les droits le permettent ; sinon fournir le contenu exact à reporter, sans prétendre qu'une synchronisation a eu lieu.

## Critère de réussite

Nous devons gagner en **compréhension et responsabilité**, pas seulement en vitesse, en volume de commentaires ou en quantité de documentation.

**Première étape demandée :** analyse critique de l'agent MR existant, proposition d'intégration du contrôle « review readiness » et de la synthèse « ce que j'ai compris », sans modifier l'agent avant accord.
