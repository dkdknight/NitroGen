# Informations sur les Jeux et l'Entraînement

## Jeux Supportés

NitroGen est un modèle de fondation entraîné sur un vaste ensemble de données de gameplay vidéo-action assemblé à partir de vidéos internet. Le modèle a été entraîné sur du contenu de jeu diversifié et peut se généraliser à divers jeux grâce à sa compréhension visuelle et ses capacités de prédiction d'actions.

### Jeux Montrés dans les Exemples

Le dépôt démontre le fonctionnement du modèle avec plusieurs jeux :
- **Celeste** (`celeste.exe`) - Exemple par défaut dans play.py
- **The Binding of Isaac: Afterbirth+** (`isaac-ng.exe`) - Nécessite une initialisation spéciale
- **Cuphead** (`Cuphead.exe`) - Nécessite une initialisation spéciale

Ce sont des exemples de jeux qui fonctionnent avec le modèle, mais le modèle n'est pas limité à ces seuls jeux.

### Informations sur l'Ensemble de Données

Pour des informations détaillées sur l'ensemble de données d'entraînement, incluant :
- Liste complète des jeux dans les données d'entraînement
- Statistiques et composition de l'ensemble de données
- Méthodologie de collecte des données

Veuillez consulter les ressources officielles :
- **Ensemble de données** : [nvidia/NitroGen sur HuggingFace](https://huggingface.co/datasets/nvidia/NitroGen)
- **Article** : [Article NitroGen](https://nitrogen.minedojo.org/assets/documents/nitrogen.pdf)
- **Site web** : [nitrogen.minedojo.org](https://nitrogen.minedojo.org/)

## Compatibilité des Jeux

NitroGen fonctionne avec les jeux qui :
- Fonctionnent sur Windows
- Acceptent les entrées de manette (émulation de contrôleur Xbox)
- Peuvent être capturés via la capture d'écran
- Ont une interface visuelle cohérente

Le modèle prend des entrées en pixels (images 256x256) et prédit des actions de manette, le rendant potentiellement compatible avec n'importe quel jeu Windows répondant à ces critères.

## Entraînement sur de Nouveaux Jeux

**Note Importante** : Ce dépôt **n'inclut pas de code d'entraînement**. Il s'agit d'une implémentation pour l'inférence uniquement.

Le processus d'entraînement implique :
1. Collecter des données de gameplay vidéo-action
2. Prétraiter les vidéos et extraire les actions
3. Entraîner ou affiner le modèle en utilisant le clonage de comportement

### Adaptation Post-Entraînement

Selon la description du projet, NitroGen "peut être adapté via post-entraînement à des jeux non vus." Cela suggère que le modèle peut être affiné sur de nouveaux jeux, mais l'infrastructure d'entraînement n'est pas incluse dans ce dépôt.

### Pour l'Entraînement/l'Affinage

Si vous devez entraîner ou affiner NitroGen sur différents jeux, vous devrez :

1. **Préparer Votre Ensemble de Données** :
   - Collecter des vidéos de gameplay du jeu cible
   - Enregistrer les actions de manette correspondantes
   - Formater les données selon le format d'entrée attendu du modèle
   - L'ensemble de données doit inclure des séquences d'images et des labels d'actions

2. **Mettre en Place l'Infrastructure d'Entraînement** :
   - Le dépôt actuel fournit uniquement le code d'inférence
   - Vous devrez implémenter ou obtenir le code d'entraînement séparément
   - L'entraînement nécessite des ressources de calcul importantes (GPU)

3. **Contacter les Auteurs** :
   - Pour accéder au code d'entraînement ou obtenir des conseils sur l'affinage
   - Pour des opportunités de collaboration
   - Visitez le [site web du projet](https://nitrogen.minedojo.org/) pour les informations de contact

4. **Référencer l'Architecture** :
   - L'architecture du modèle est définie dans `nitrogen/flow_matching_transformer/nitrogen.py`
   - La configuration est disponible dans `nitrogen/cfg.py`
   - Étudiez ces fichiers pour comprendre la structure du modèle

## Exécuter l'Inférence sur Différents Jeux

Bien que vous ne puissiez pas entraîner le modèle avec ce dépôt, vous pouvez essayer d'exécuter l'inférence sur différents jeux :

1. **Démarrer le serveur d'inférence** :
   ```bash
   python scripts/serve.py <chemin_vers_ng.pt>
   ```

2. **Exécuter l'agent sur votre jeu** :
   ```bash
   python scripts/play.py --process '<VotreJeu.exe>'
   ```

3. **Conseils pour de meilleurs résultats** :
   - Utilisez des jeux visuellement ou mécaniquement similaires aux données d'entraînement
   - Assurez-vous que la fenêtre du jeu est clairement visible et non obstruée
   - Commencez avec le jeu dans un état simple et initial
   - Le modèle fonctionne mieux avec des jeux nécessitant des entrées de manette

## Conditionnement par Jeu

Le modèle supporte le conditionnement spécifique au jeu lorsqu'il est disponible. Lors de l'inférence, vous pouvez sélectionner un ID de jeu spécifique si le modèle a été entraîné avec des labels de jeu. Cela aide le modèle à adapter son comportement au jeu spécifique joué.

## Limitations

- **Pas de Code d'Entraînement** : Ce dépôt fournit uniquement l'inférence
- **Windows Uniquement** : Les environnements de jeu doivent fonctionner sur Windows
- **Disponibilité des Jeux** : Vous devez fournir vos propres copies de jeux obtenues légalement
- **Performance Variable** : La performance du modèle dépend de la similarité avec les données d'entraînement

## Recherche et Développement

Ce projet est strictement à des fins de recherche. Pour :
- Applications commerciales
- Entraînement sur des jeux propriétaires
- Accès à l'infrastructure d'entraînement
- Développement de modèles personnalisés

Veuillez vous référer à la licence et contacter l'équipe de recherche via les canaux officiels.

## Ressources Supplémentaires

- **Poids du Modèle** : [nvidia/NitroGen sur HuggingFace](https://huggingface.co/nvidia/NitroGen)
- **Article de Recherche** : Disponible sur [nitrogen.minedojo.org](https://nitrogen.minedojo.org/)
- **Suivi des Problèmes** : Signalez des bugs ou posez des questions sur le [dépôt GitHub](https://github.com/MineDojo/NitroGen)

## Citation

Si vous utilisez NitroGen dans votre recherche, veuillez citer :

```bibtex
@misc{Magne2025NitroGen,
  title        = {NitroGen: An Open Foundation Model for Generalist Gaming Agents},
  author       = {Magne, Lo{\"\i}c and Awadalla, Anas and Wang, Guanzhi and Xu, Yinzhen and Belofsky, Joshua and Hu, Fengyuan and Kim, Joohwan and Schmidt, Ludwig and Gkioxari, Georgia and Kautz, Jan and Yue, Yisong and Choi, Yejin and Zhu, Yuke and Fan, Linxi},
  year         = {2025},
  howpublished = {\url{https://nitrogen.minedojo.org/}},
}
```

---

## Réponse Directe aux Questions

### Sur quels jeux est-il entraîné ?

Le modèle NitroGen est entraîné sur un vaste ensemble de données de gameplay assemblé à partir de vidéos internet. Pour la liste complète et détaillée des jeux dans l'ensemble d'entraînement, consultez :
- L'ensemble de données sur [HuggingFace](https://huggingface.co/datasets/nvidia/NitroGen)
- L'article de recherche sur le [site web du projet](https://nitrogen.minedojo.org/)

Les exemples dans ce dépôt montrent qu'il fonctionne avec des jeux comme Celeste, The Binding of Isaac et Cuphead, mais le modèle a été exposé à beaucoup plus de jeux pendant l'entraînement.

### Comment l'entraîner sur d'autres jeux ?

**Ce dépôt ne contient pas de code d'entraînement**. Il s'agit d'une implémentation d'inférence uniquement. Pour entraîner ou affiner le modèle sur d'autres jeux :

1. **Collectez des Données** : Enregistrez des vidéos de gameplay avec les actions de manette correspondantes
2. **Obtenez le Code d'Entraînement** : Contactez les auteurs ou consultez l'article pour plus de détails sur l'infrastructure d'entraînement
3. **Ressources Nécessaires** : L'entraînement nécessite des GPU puissants et une expertise en apprentissage profond
4. **Alternative** : Vous pouvez essayer d'exécuter le modèle pré-entraîné sur de nouveaux jeux sans ré-entraînement - le modèle peut généraliser à des jeux similaires visuellement ou mécaniquement

Pour plus d'informations sur l'entraînement ou des collaborations, visitez le site web du projet et contactez l'équipe de recherche.
