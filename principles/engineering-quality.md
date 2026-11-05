# Qualité d'ingénierie

Nous visons une qualité **adaptée au risque**, pas un idéal stylistique.

1. **Fonctionnel explicite :** le comportement attendu doit pouvoir être vérifié. Si le besoin est ambigu, ne pas inventer une règle métier en silence.
2. **Sécurité et intégrité :** aucun compromis implicite sur les autorisations, données, transactions ou effets irréversibles.
3. **Maintenabilité :** préférer la simplicité compréhensible, détecter la complexité sans justification et éviter la dette importante cachée.
4. **Preuves adaptées :** distinguer test automatisé exécuté, vérification manuelle et hypothèse non vérifiée.
5. **Proportionnalité :** une petite correction n'exige pas le même contrôle qu'une migration de données ou une modification de permissions.
6. **Décisions explicites :** les exceptions et risques acceptés ont un responsable identifiable.

La préférence du reviewer pour une implémentation « plus élégante » ne suffit pas à bloquer une MR. Inversement, « les tests passent » ne suffit pas si un risque significatif est connu et non traité.
