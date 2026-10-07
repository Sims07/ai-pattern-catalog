# ⚡ AI Architecture Patterns & Enterprise FinOps Catalog

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Stack](https://img.shields.io/badge/Stack-Spring%20Boot%203%20%7C%20Kafka%20%7C%20Gravitee-5e6ad2.svg)](#-stack-entreprise-de-référence)
[![UI Framework](https://img.shields.io/badge/UI-Alpine.js%20%2B%20Tailwind-black.svg)](https://tailwindcss.com)

Un catalogue d'architecture interactif, moderne et épuré (style **Linear UI**) conçu pour les **Architectes SI, Tech Leads et Product Owners**. Il centralise les directives de conception, les arbitrages techniques et les optimisations **FinOps** pour les workloads d'IA Générative et LLM en entreprise.

---

## 🎯 Objectifs du Projet

L'intégration de l'IA Générative au sein des SI d'entreprise apporte des défis majeurs : maîtrise des coûts API (FinOps), souveraineté & confidentialité des données (PII/RGPD), gouvernance API et latence.

Ce catalogue offre un référentiel visuel et opérationnel permettant de :
- **Standardiser les motifs d'architecture (Patterns)** pour l'intégration des LLM et RAG.
- **Accélérer les arbitrages techniques** grâce à un comparateur matriciel d'Architecture Decision Records (**ADR**).
- **Simuler et optimiser la facture API LLM** à l'aide d'un calculateur FinOps dynamique.
- **Aligner les équipes Métier, Produit et Engineering** via un glossaire contextuel.

---

## ✨ Fonctionnalités Principales

### 1. 🗂️ Catalogue des Patterns IA
- **Filtres et recherche dynamique** : Recherche par mots-clés (moteur, outils, problématiques) et filtres par catégories (*RAG, FinOps, Agents, Sécurité/PII, Observabilité, Fine-Tuning*).
- **Fiches détaillées par Pattern** :
  - Contextualisation et problématique métier.
  - Solution technique & **flux architectural (Sequence Flow)**.
  - Métriques d'observabilité clés (*TTFT, Hit Rate, Accuracy*).
  - Découpage applicatif sur la stack entreprise de référence (**Gravitee API Gateway, Apache Kafka, Spring Boot 3**).

### 2. ⚖️ Comparateur d'Architecture & Générateur ADR
- Sélection côte à côte de 2 à 4 patterns pour arbitrer les compromis (*Trade-offs*).
- Matrice comparative : Complexité, Latence, Impact FinOps, Rôle Gateway et Stack requise.
- **Export en un clic au format Markdown ADR** (Architecture Decision Record) prêt à être collé dans Git ou Confluence.

### 3. 🧮 Simulateur de Coûts FinOps
- Calculateur de rentabilité pour mesurer l'impact financier de l'activation des patterns :
  - **Semantic Caching (Redis VL)** (-30% de requêtes redondantes)
  - **LLM Router / Cascading** (-60% de bascule vers des modèles SLM/économiques)
  - **Prompt Compression** (-20% de jetons consommés)
- Visualisation de l'économie mensuelle et annuelle réévaluée.

### 4. 📖 Glossaire & Vulgarisation IA
- Dictionnaire de termes techniques (*RAG Triad, Vector Embedding, Speculative Decoding, LoRA, TTFT, PII Vaulting*).
- **Contextualisation Architecte** pour expliquer simplement l'enjeu SI de chaque concept.

---

## 🏛️ Stack Entreprise de Référence

Le catalogue décline chaque pattern selon une architecture hybride événementielle et contrôlée :

```
[ Client / Web ] ──► [ Gravitee API Gateway ] (OAuth2, Rate-limiting, Policy PII, Semantic Cache)
                             │
                             ▼
                    [ Spring Boot 3 Microservice ] (Spring AI / LangChain4j)
                             │
                             ├─► [ Apache Kafka Stream ] (Event Sourcing & Ingestion RAG)
                             └─► [ Vector DB / LLM Providers ] (Pgvector, Redis, OpenAI/Ollama)
```

- **Gravitee API Gateway** : Gestion de la sécurité au périmètre, contrôles de quota, masquage PII et caching vecteur de premier niveau.
- **Apache Kafka** : Streaming d'événements pour l'ingestion asynchrone de documents, la re-vectorisation et le tracing audit.
- **Spring Boot 3 (Spring AI / LangChain4j)** : Microservices réactifs Java assurant l'orchestration métier, les appels de fonctions (*Tool Calling*) et les pipelines RAG.

---

## 🚀 Prise en main rapide

Aucune étape de compilation ni installation complexe n'est requise. L'application est contenue dans un **fichier unique auto-hébergé (`index.html`)**.

### Option A : Utilisation directe
Ouvrez simplement le fichier `index.html` dans votre navigateur Web moderne.

### Option B : Serveur local léger
```bash
# Clonez le dépôt
git clone https://github.com/votre-compte/ai-architecture-patterns.git
cd ai-architecture-patterns

# Lancement avec Python
python3 -m http.server 8080

# Accédez à http://localhost:8080 dans votre navigateur
```

---

## 🛠️ Stack Technique Frontend

L'interface a été conçue sans dépendances lourdes type NPM/Node pour une portabilité maximale :
- **HTML5 & Tailwind CSS** (via CDN avec configuration sur-mesure pour le thème sombre *Linear UI*).
- **Alpine.js 3.x** : Framework réactif léger pour la gestion d'état locale (changement de vues, filtres, comparateur, modal et calculateur).
- **Lucide Icons** : Pack d'icônes vectorielles épurées.
- **JetBrains Mono & Inter** : Typographies optimisées pour la lisibilité du code et des tableaux de données.

---

## 📄 Exemple de Fiche ADR Exportée

Voici la structure générée automatiquement par le bouton **"Copier la fiche ADR (Markdown)"** :

```markdown
# Architecture Decision Record (ADR) - Async PII Scrubbing & Vaulting Pipeline

## Statut
Proposé / Validé

## Contexte & Problématique Métier
Traitement de documents juridiques, RH ou bancaires contenant des données PII ne devant jamais quitter le réseau souverain.

## Pattern d'Architecture Retenu
Extraction de texte, détection NER des entités sensibles, remplacement par des UUIDs enregistrés dans un Vault.

## Implémentation Entreprise Stack Standard
- **Gravitee API Gateway**: Policy de filtrage et contrôle regex sur headers/payload HTTP.
- **Apache Kafka Stream**: Microservice Redactor à l’écoute du topic raw-documents-v1.
- **Spring Boot 3 & Java Stack**: Application Spring Boot 3 avec @KafkaListener et SDK Presidio Java.

## Impact FinOps & Stratégie de Coûts
- **Niveau d'impact**: High
- **Détails**: Évite les sanctions RGPD massives et réduit la taille du contexte.
```

---

## 🤝 Contribution

Les contributions sont les bienvenues ! Vous pouvez proposer de nouveaux patterns, améliorer le calculateur FinOps ou enrichir le glossaire :
1. Forkez le projet.
2. Créez votre branche d'itération (`git checkout -b feature/nouveau-pattern-ia`).
3. Commitez vos modifications (`git commit -m 'Add: Pattern GraphRAG Hybrid'`).
4. Pushez vers la branche (`git push origin feature/nouveau-pattern-ia`).
5. Ouvrez une **Pull Request**.

---

## 📜 Licence

Ce projet est sous licence **MIT**. Vous êtes libre de le réutiliser, le modifier et l'intégrer dans vos environnements d'entreprise.