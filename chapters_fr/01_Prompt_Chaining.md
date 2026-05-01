# Chapitre 1 : Chaînage de Prompts (Prompt Chaining)

## Aperçu du pattern

Le **chaînage de prompts** (parfois appelé pattern Pipeline) est un paradigme puissant pour traiter des tâches complexes avec les LLMs. Au lieu d'attendre d'un LLM qu'il résolve un problème complexe en une seule étape monolithique, le chaînage de primes propose une stratégie **diviser pour régner**.

L'idée centrale : décomposer le problème original en une **séquence de sous-problèmes plus petits et gestionnables**. Chaque sous-problème est traité par un prompt spécifiquement conçu, et la sortie d'un prompt est transmise comme entrée au prompt suivant dans la chaîne.

### Pourquoi le chaînage ?

Les limites d'un prompt unique pour les tâches complexes :
- **Négligence d'instructions** : le modèle ignore certaines parties du prompt
- **Dérive contextuelle** : le modèle perd le fil du contexte initial
- **Propagation d'erreurs** : les erreurs précoces s'amplifient
- **Surcharge cognitive** : augmente les risques d'hallucination

La décomposition séquentielle améliore significativement la fiabilité et le contrôle.

### Exemple concret

Une requête demandant d'analyser un rapport de marché, résumer les conclusions, identifier les tendances avec des données chiffrées, et rédiger un email — risque d'échouer en un seul prompt.

**Approche chaînée :**

1. **Prompt 1 (Résumé)** : « Résume les conclusions clés du rapport de marché suivant : [texte]. » — Le modèle se concentre uniquement sur le résumé.
2. **Prompt 2 (Identification de tendances)** : « En utilisant le résumé, identifie les trois principales tendances émergentes et extrais les données chiffrées qui soutiennent chaque tendance : [sortie de l'étape 1]. » — Ce prompt est plus contraint et s'appuie sur une sortie validée.
3. **Prompt 3 (Rédaction d'email)** : « Rédige un email concis à l'équipe marketing présentant les tendances suivantes et leurs données : [sortie de l'étape 2]. »

Chaque étape est plus simple et moins ambiguë, ce qui réduit la charge cognitive du modèle et mène à un résultat final plus précis et fiable.

### Le rôle du format de sortie structuré

La fiabilité d'une chaîne de prompts dépend fortement de l'intégrité des données transmises entre les étapes. Spécifier un **format de sortie structuré** (JSON, XML) est crucial pour éviter les ambiguïtés.

Exemple de sortie structurée en JSON :
```json
{
  "trends": [
    {
      "trend_name": "Personnalisation par l'IA",
      "supporting_data": "73% des consommateurs préfèrent faire affaire avec des marques qui utilisent leurs informations personnelles pour rendre leur expérience plus pertinente."
    },
    {
      "trend_name": "Marques durables et éthiques",
      "supporting_data": "Les ventes de produits avec des critères ESG ont augmenté de 28% sur les cinq dernières années."
    }
  ]
}
```

Ce format structuré garantit que les données sont lisibles par la machine et peuvent être analysées et insérées sans ambiguïté dans le prompt suivant.

---

## Applications pratiques & Cas d'usage

### 1. Flux de traitement de l'information

Transformer de l'information brute à travers de multiples étapes :
- Prompt 1 : Extraire le contenu textuel d'une URL ou d'un document
- Prompt 2 : Résumer le texte nettoyé
- Prompt 3 : Extraire des entités spécifiques (noms, dates, lieux)
- Prompt 4 : Utiliser les entités pour interroger une base de connaissances
- Prompt 5 : Générer un rapport final intégrant résumé, entités et résultats

Domaines : analyse de contenu automatisée, assistants de recherche IA, génération de rapports complexes.

### 2. Réponse à des requêtes complexes

Questions nécessitant plusieurs étapes de raisonnement ou de récupération d'information. Exemple : « Quelles étaient les causes principales du krach boursier de 1929 et comment la politique gouvernementale y a-t-elle répondu ? »

- Prompt 1 : Identifier les sous-questions (causes, réponse gouvernementale)
- Prompt 2 : Rechercher les causes du krach de 1929
- Prompt 3 : Rechercher la réponse politique au krach
- Prompt 4 : Synthétiser les informations des étapes 2 et 3

Combinaison fréquente : **traitement parallèle** pour la collecte de données indépendante + **chaînage de prompts** pour les étapes dépendantes de synthèse et raffinement.

### 3. Extraction et transformation de données

Conversion de texte non structuré en format structuré, avec itérations :
- Prompt 1 : Extraire les champs spécifiques d'une facture
- Traitement : Vérifier si tous les champs requis ont été extraits
- Prompt 2 (conditionnel) : Si des champs manquent, demander au modèle de les trouver spécifiquement
- Sortie : Données structurées validées

Cas d'usage OCR : extraction de texte → normalisation des données (« mille cinquante » → 1050) → délégation des calculs arithmétiques à un outil externe.

### 4. Flux de génération de contenu

Composition de contenu complexe décomposée en phases distinctes :
- Prompt 1 : Générer 5 idées de sujets
- Prompt 2 : Générer un plan détaillé pour le sujet sélectionné
- Prompt 3 : Rédiger une section basée sur le premier point du plan
- Prompt 4 : Rédiger la section suivante avec contexte de la précédente
- Prompt 5 : Réviser et affiner le brouillon complet

### 5. Agents conversationnels avec état

Le chaînage de prompts fournit un mécanisme fondamental pour préserver la continuité conversationnelle en intégrant les informations des interactions précédentes dans chaque nouveau tour.

### 6. Génération et raffinement de code

Processus multi-étapes pour la production de code :
- Comprendre la requête → Générer du pseudocode → Écrire le brouillon de code → Identifier les erreurs → Raffiner → Ajouter documentation et tests

L'insertion de **logique déterministe** entre les appels au modèle permet la validation, le traitement intermédiaire et la ramification conditionnelle.

### 7. Raisonnement multimodal et multi-étapes

Analyse de données avec des modalités diverses (image + texte intégré + tableau) nécessite une décomposition en tâches basées sur des prompts spécialisés.

---

## Exemple de code pratique (LangChain)

```python
import os
from langchain_openai import ChatOpenAI
from langchain_core.prompts import ChatPromptTemplate
from langchain_core.output_parsers import StrOutputParser

# Initialiser le modèle de langage
llm = ChatOpenAI(temperature=0)

# --- Prompt 1 : Extraire les informations ---
prompt_extract = ChatPromptTemplate.from_template(
    "Extrais les spécifications techniques du texte suivant :\n\n{text_input}"
)

# --- Prompt 2 : Transformer en JSON ---
prompt_transform = ChatPromptTemplate.from_template(
    "Transforme les spécifications suivantes en objet JSON avec les clés 'cpu', 'memory' et 'storage' :\n\n{specifications}"
)

# --- Construire la chaîne avec LCEL ---
extraction_chain = prompt_extract | llm | StrOutputParser()

full_chain = (
    {"specifications": extraction_chain}
    | prompt_transform
    | llm
    | StrOutputParser()
)

# --- Exécuter la chaîne ---
input_text = "Le nouveau modèle de laptop dispose d'un processeur octa-core 3.5 GHz, 16 Go de RAM et un SSD NVMe de 1 To."

final_result = full_chain.invoke({"text_input": input_text})

print("\n--- Sortie JSON finale ---")
print(final_result)
```

Installation des dépendances :
```bash
pip install langchain langchain-community langchain-openai langgraph
```

---

## Ingénierie du Contexte vs Ingénierie des Prompts

L'**ingénierie du contexte** (*Context Engineering*) est la discipline systématique de conception, construction et livraison d'un **environnement informationnel complet** au modèle IA avant la génération de tokens. Elle affirme que la qualité de la sortie dépend moins de l'architecture du modèle et davantage de la **richesse du contexte fourni**.

C'est une évolution significative par rapport à l'ingénierie des prompts traditionnelle, qui se concentre principalement sur l'optimisation de la formulation de la requête immédiate de l'utilisateur.

### Couches d'information du contexte :

| Couche | Description | Exemple |
|--------|-------------|---------|
| **Prompt système** | Instructions fondamentales définissant les paramètres opérationnels | « Tu es un rédacteur technique ; ton ton doit être formel et précis. » |
| **Données récupérées** | Documents tirés d'une base de connaissances | Spécifications techniques pour un projet |
| **Sorties d'outils** | Résultats d'APIs externes en temps réel | Disponibilité du calendrier utilisateur |
| **Données implicites** | Identité utilisateur, historique, état environnemental | Relation professionnelle avec le destinataire |

Principe : même les modèles avancés sous-performent avec un contexte limité ou mal construit. L'ingénierie du contexte transforme la tâche de « répondre à une question » en **construire un tableau opérationnel complet** pour l'agent.

---

## En un coup d'œil

**Quoi** : Les tâches complexes submergent les LLMs en un seul prompt — négligence d'instructions, dérive contextuelle, hallucinations.

**Pourquoi** : Le chaînage décompose le problème en sous-tâches interconnectées. Chaque étape utilise un prompt focalisé, la sortie d'un prompt alimente le suivant. Stratégie modulaire diviser-pour-régner rendant le processus plus gérable et débogable.

**Règle empirique** : Utiliser ce pattern quand une tâche est trop complexe pour un seul prompt, implique des étapes de traitement distinctes, nécessite l'interaction avec des outils externes entre les étapes, ou nécessite un raisonnement multi-étapes avec gestion d'état.

---

## Points clés

- Le **chaînage de prompts** décompose les tâches complexes en une séquence d'étapes focalisées — parfois appelé pattern Pipeline
- Chaque étape implique un appel LLM ou une logique de traitement, utilisant la sortie de l'étape précédente comme entrée
- Ce pattern améliore la **fiabilité** et la **gérabilité** des interactions complexes avec les modèles de langage
- Les frameworks comme **LangChain/LangGraph** et **Google ADK** fournissent des outils robustes pour définir, gérer et exécuter ces séquences multi-étapes

---

## Conclusion

En déconstruisant les problèmes complexes en sous-tâches plus simples et gérables, le chaînage de prompts fournit un cadre robuste pour guider les LLMs. Cette stratégie « diviser pour régner » améliore significativement la fiabilité et le contrôle de la sortie. En tant que pattern fondamental, il permet le développement d'agents IA sophistiqués capables de raisonnement multi-étapes, d'intégration d'outils et de gestion d'état. Maîtriser le chaînage de prompts est crucial pour construire des systèmes robustes et sensibles au contexte.

---

*Source : Chapitre 1 de « Agentic Design Patterns » par Antonio Gulli — Pages 21-33*