# 📚 Agentic Design Patterns — Guide Pratique pour Construire des Systèmes Intelligents

[![Livre](https://img.shields.io/badge/Livre-Pr%C3%A9--commande-blue)](https://www.amazon.com/Agentic-Design-Patterns-Hands-Intelligent/dp/3032014018/)
[![Auteur](https://img.shields.io/badge/Auteur-Antonio%20Gulli-green)](https://www.linkedin.com/in/searchguy/)
[![Charité](https://img.shields.io/badge/Royalties-Save%20the%20Children-red)](https://www.savethechildren.org/)
[![Licence](https://img.shields.io/badge/Licence-%C3%89ducatif-yellow)]()

> 🇬🇧 [English version](README.md) | 🇫🇷 **Version française**

## 📖 À propos de ce dépôt

Ce dépôt contient les matériaux complets pour **« Agentic Design Patterns : A Hands-On Guide to Building Intelligent Systems »** d'Antonio Gulli. Il comprend tous les chapitres en format PDF et les notebooks de code accompagnateurs pour un apprentissage pratique.

> **Note** : La totalité des droits d'auteur est reversée à Save the Children 💝

## 🎯 Ce que vous apprendrez

Ce guide complet couvre 21 chapitres et 7 annexes sur la construction de systèmes d'agents IA intelligents :

- **Motifs fondamentaux** : Chaînage de prompts, routage, parallélisation
- **Techniques avancées** : Réflexion, utilisation d'outils, planification, systèmes multi-agents
- **Mémoire & Apprentissage** : Gestion de la mémoire, adaptation, définition d'objectifs
- **Motifs de production** : Gestion des exceptions, humain-dans-la-boucle, RAG
- **Optimisation** : Motifs tenant compte des ressources, techniques de raisonnement, garde-fous
- **Applications réelles** : De l'interface graphique aux environnements du monde réel

## 📁 Structure du dépôt

```
.
├── 📄 README.md                           # Ce fichier
├── 📄 README_FR.md                        # Version française
├── 📚 book/
│   └── Agentic_Design_Patterns_Complete.pdf  # Livre complet (424 pages)
├── 💻 chapter_notebooks/                  # Notebooks par chapitre
│   ├── Chapter_01_Prompt_Chaining.ipynb
│   ├── Chapter_02_Routing.ipynb
│   ├── Chapter_03_Parallelization.ipynb
│   ├── ...
│   └── Appendix_G_Coding_Agents.ipynb
```

## 📚 Table des matières

### Introduction & Fondements
- Dédicace
- Remerciements
- Avant-propos
- Perspectives d'un leader d'opinion : Pouvoir et Responsabilité
- Introduction
- Qu'est-ce qui fait d'un système IA un « agent » ?

### Première partie : Motifs fondamentaux (103 pages)
1. **Chapitre 1** : Chaînage de prompts — Décomposition séquentielle des tâches
2. **Chapitre 2** : Routage — Sélection dynamique de chemin
3. **Chapitre 3** : Parallélisation — Traitement concurrent
4. **Chapitre 4** : Réflexion — Mécanismes d'auto-amélioration
5. **Chapitre 5** : Utilisation d'outils — Intégration de capacités externes
6. **Chapitre 6** : Planification — Gestion stratégique des tâches
7. **Chapitre 7** : Multi-Agent — Systèmes collaboratifs

### Deuxième partie : Motifs avancés (61 pages)
8. **Chapitre 8** : Gestion de la mémoire — Persistance de l'état
9. **Chapitre 9** : Apprentissage et Adaptation — Amélioration dynamique
10. **Chapitre 10** : Model Context Protocol (MCP) — Interfaces standardisées
11. **Chapitre 11** : Définition et Suivi d'Objectifs — Suivi des objectifs

### Troisième partie : Motifs de production (34 pages)
12. **Chapitre 12** : Gestion des Exceptions et Récupération — Gestion robuste des erreurs
13. **Chapitre 13** : Humain-dans-la-Boucle — Collaboration humain-IA
14. **Chapitre 14** : Récupération de Connaissances (RAG) — Motifs d'accès à l'information

### Quatrième partie : Motifs d'entreprise (114 pages)
15. **Chapitre 15** : Communication Inter-Agent (A2A) — Réseau d'agents
16. **Chapitre 16** : Optimisation Tenant Compte des Ressources — Utilisation efficace des ressources
17. **Chapitre 17** : Techniques de Raisonnement — Prise de décision avancée
18. **Chapitre 18** : Garde-fous / Motifs de Sécurité — Atténuation des risques
19. **Chapitre 19** : Évaluation et Surveillance — Suivi des performances
20. **Chapitre 20** : Priorisation — Gestion des tâches
21. **Chapitre 21** : Exploration et Découverte — Apprentissage autonome

### Annexes (74 pages)
- **Annexe A** : Techniques de prompting avancées
- **Annexe B** : IA Agentique : De l'interface graphique à l'environnement réel
- **Annexe C** : Vue d'ensemble rapide des frameworks agentiques
- **Annexe D** : Construire un agent avec AgentSpace
- **Annexe E** : Agents IA en ligne de commande
- **Annexe F** : Sous le capot : Moteurs de raisonnement
- **Annexe G** : Agents de codage

### Conclusion & Références
- Conclusion
- Glossaire
- Index des termes

## 🚀 Pour commencer

### Prérequis

```bash
# Python 3.8 ou supérieur requis
python --version

# Installer Jupyter pour les notebooks
pip install jupyter notebook

# Installer les dépendances courantes
pip install -r requirements.txt
```

### Installation

1. **Cloner le dépôt**
```bash
git clone https://github.com/evoiz/Agentic-Design-Patterns.git
cd Agentic-Design-Patterns
```

2. **Configurer l'environnement virtuel** (recommandé)
```bash
python -m venv venv
source venv/bin/activate  # Sur Windows : venv\Scripts\activate
```

3. **Installer les dépendances**
```bash
pip install jupyter notebook
pip install pandas numpy matplotlib openai langchain
```

4. **Lancer Jupyter Notebook**
```bash
jupyter notebook
```

## 💻 Exécuter le code

Chaque chapitre inclut un notebook Jupyter avec des exemples pratiques :

1. Naviguer vers le répertoire `chapter_notebooks/`
2. Ouvrir le notebook du chapitre souhaité
3. Suivre les instructions dans chaque notebook
4. Exécuter les cellules séquentiellement pour une meilleure expérience d'apprentissage

### Exemple : Exécuter le Chapitre 1
```python
# Naviguer vers le répertoire des notebooks
cd chapter_notebooks

# Lancer un notebook spécifique
jupyter notebook Chapter_01_Prompt_Chaining.ipynb
```

## 📖 Comment utiliser ce dépôt

### Pour l'apprentissage autonome
1. Lire chaque chapitre dans le PDF
2. Ouvrir le notebook correspondant
3. Exécuter les exemples de code
4. Expérimenter avec des modifications
5. Compléter les exercices

### Pour l'enseignement
1. Utiliser les chapitres comme support de cours
2. Assigner les notebooks comme travaux pratiques
3. Créer des exemples personnalisés basés sur les motifs
4. Construire des projets utilisant plusieurs motifs

### Pour la recherche
1. Référencer les motifs d'implémentation
2. Comparer différentes approches
3. Étendre les motifs pour de nouveaux cas d'usage
4. Contribuer des améliorations

## 🤝 Contribuer

Les contributions sont les bienvenues ! Consultez nos [Directives de contribution](CONTRIBUTING.md).

### Comment contribuer
- 🐛 Signaler des bugs et des problèmes
- 💡 Suggérer de nouvelles fonctionnalités ou motifs
- 📝 Améliorer la documentation
- 🔧 Soumettre des améliorations de code
- 🌍 Traduire les matériaux

### Processus de contribution
1. Forker le dépôt
2. Créer une branche de fonctionnalité (`git checkout -b feature/AmazingFeature`)
3. Commiter les changements (`git commit -m 'Add some AmazingFeature'`)
4. Pousser vers la branche (`git push origin feature/AmazingFeature`)
5. Ouvrir une Pull Request

## 📚 Ressources supplémentaires

### Liens officiels
- 📖 [Pré-commander le livre](https://www.amazon.com/Agentic-Design-Patterns-Hands-Intelligent/dp/3032014018/)
- 👨‍💼 [LinkedIn de l'auteur](https://www.linkedin.com/in/searchguy/)
- 📁 [Matériaux Google Drive originaux](https://drive.google.com/drive/u/0/folders/1Y3U3IrYCiJ3E45Z8okR5eCg7OPnWQtPV)

### Frameworks associés
- [LangChain](https://langchain.com/)
- [AutoGPT](https://github.com/Significant-Gravitas/AutoGPT)
- [OpenAI Assistants](https://platform.openai.com/assistants)
- [Microsoft AutoGen](https://github.com/microsoft/autogen)
- [CrewAI](https://www.crewai.com/)

### Parcours d'apprentissage
1. **Débutants** : Commencer par les Chapitres 1-7 (Motifs fondamentaux)
2. **Intermédiaires** : Progresser avec les Chapitres 8-14 (Avancé & Production)
3. **Avancés** : Maîtriser les Chapitres 15-21 (Motifs d'entreprise)
4. **Experts** : Explorer les Annexes pour les techniques de pointe

## ⚖️ Licence

Ce dépôt est destiné à des fins éducatives. Veuillez respecter les droits d'auteur et la propriété intellectuelle de l'auteur.

- **Contenu du livre** : © Antonio Gulli — Tous droits réservés
- **Exemples de code** : Licence MIT (voir le fichier LICENSE)
- **Usage éducatif** : Autorisé avec attribution

## 🙏 Remerciements

- **Antonio Gulli** — Auteur et leader de pensée en IA
- **Save the Children** — Bénéficiaire de l'intégralité des droits d'auteur
- **Contributeurs** — Tous ceux qui aident à améliorer ces matériaux
- **Communauté** — Apprenants et praticiens qui font avancer les agents IA

## 📞 Contact & Support

- **Problèmes** : [GitHub Issues](https://github.com/evoiz/Agentic-Design-Patterns/issues)
- **Discussions** : [GitHub Discussions](https://github.com/evoiz/Agentic-Design-Patterns/discussions)
- **Auteur** : [LinkedIn](https://www.linkedin.com/in/searchguy/)

## 🌟 Historique des étoiles

Si vous trouvez ce dépôt utile, pensez à lui donner une étoile ⭐

[![Graphique de l'historique des étoiles](https://api.star-history.com/svg?repos=evoiz/agentic-design-patterns&type=Date)](https://star-history.com/#evoiz/agentic-design-patterns&Date)

## 📊 Statistiques du dépôt

![Dernier commit GitHub](https://img.shields.io/github/last-commit/evoiz/agentic-design-patterns)
![Issues GitHub](https://img.shields.io/github/issues/evoiz/agentic-design-patterns)
![Pull requests GitHub](https://img.shields.io/github/issues-pr/evoiz/agentic-design-patterns)
![Licence GitHub](https://img.shields.io/github/license/evoiz/agentic-design-patterns)

---

<p align="center">
  <strong>Construire l'avenir de l'IA, un motif à la fois 🚀</strong>
</p>

<p align="center">
  Fait avec ❤️ pour la communauté IA
</p>