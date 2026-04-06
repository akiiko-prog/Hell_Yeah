# 🧠 PROJECT: NEURAL-STRYKE (Personal Intelligence Engine)

## 🎯 Vision
Créer une infrastructure cognitive auto-hébergée (NAS) capable d'absorber, de lier et de restituer toute forme de connaissance (liens, tutos, schémas, idées) via une interface spatiale et une recherche sémantique par IA (RAG). 
*Think Jarvis, but private.*

---

## 🛠 Stack Technique (The "Masterpiece" Tools)

### 1. Core Engine (Intelligence & Memory)
* **Ollama (Llama 3 / DeepSeek) :** Le cerveau LLM local.
* **Qdrant :** Database vectorielle pour la mémoire sémantique.
* **Danswer :** Moteur de recherche unifié (Type "Enterprise Search") pour interroger la base.

### 2. Automation & Ingestion (The Nervous System)
* **n8n (Self-hosted) :** Orchestrateur de workflow pour scrapper et tagger automatiquement les liens.
* **ArchiveBox :** Pour cloner chaque site/tuto et éviter les liens morts (Link Rot).
* **Whisper :** Pour transcrire les tutos vidéo en texte indexable.

### 3. Interface & Visualization (The Command Center)
* **Obsidian + Neo4j Plugin :** Visualisation en graphe 3D des connexions entre idées.
* **Nextcloud :** Stockage sécurisé des fichiers et schémas.
* **Tailscale :** Réseau Mesh privé pour le partage sécurisé avec l'équipe.

---

## 🏗 Architecture du Pipeline
1. **CAPTURE :** Envoi d'un lien via Bot Telegram custom.
2. **PROCESS :** n8n récupère le contenu -> ArchiveBox clone -> Ollama résume et extrait les entités (tags).
3. **STORAGE :** Markdown généré dans Nextcloud + Vecteurs injectés dans Qdrant.
4. **QUERY :** Recherche via langage naturel ("Jarvis, montre-moi mes idées de domotique").

---

## 🤝 Comment aider sur le projet ? (For the Bros)

### Setup de l'environnement :
1. Clone le repo de config Docker.
2. Assure-toi d'avoir un accès au NAS via **Tailscale**.
3. Installe **Docker Desktop** ou travaille directement sur le portail **Portainer** du NAS.

### Backlog Prioritaire :
* **Module "Vision" :** Intégrer un modèle de reconnaissance d'image pour extraire le texte des schémas techniques (OCR/VLM).
* **Module "Social" :** Configurer les permissions via **Authelia** pour que vous puissiez voir uniquement les dossiers `/shared`.
* **Module "Dashboard" :** Créer une interface Next.js ultra-rapide pour visualiser le "Graphe de Connaissance".

---

## ⚠️ Sécurité & Confidentialité
* **Zéro Cloud :** Aucune donnée ne quitte le NAS pour l'IA.
* **MFA :** Accès externe protégé par Double Authentification.
* **Backups :** Snapshot 3-2-1 automatique sur disque externe.

## 🧠 The AI Brain Setup (Zero-Cost Strategy)

Pour éviter les frais d'API Anthropic/OpenAI, nous utilisons une architecture de "Routage Fantôme" :

1. **Inference Server :** Ollama (Docker) tournant sur le NAS.
2. **Model Selection :** - `deepseek-v3` pour le brainstorming d'idées.
   - `qwen2.5-coder` pour l'analyse des schémas techniques.
3. **Claude Emulation :** Configuration de la variable `ANTHROPIC_BASE_URL` pour pointer vers notre IP locale.
   
> **Note pour l'équipe :** On ne paie RIEN. La seule limite, c'est la RAM du NAS. Si ça rame, on passe sur des versions quantifiées (GGUF) des modèles.
