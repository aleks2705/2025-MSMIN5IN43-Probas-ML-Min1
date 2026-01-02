# Conformal Prediction — 

Bref aperçu

- Projet de démonstration de prédiction conforme (MAPIE) appliquée à un modèle « boîte noire » (RandomForest) pour estimer des prix et fournir des intervalles de confiance.

Démarrer le backend (FastAPI)

1. Se placer dans le dossier backend :

   - cd backend
2. Créer et activer l'environnement virtuel :

   - Windows PowerShell:
     .venv\Scripts\Activate.ps1
   - Windows (cmd):
     .venv\Scripts\activate.bat
   - macOS / Linux:
     source .venv/bin/activate
3. Installer les dépendances :

   - pip install -r requirements.txt
     (ou pip install fastapi uvicorn pandas scikit-learn mapie joblib requests)
4. (Optionnel) Entraîner le modèle Ames si nécessaire :

   - python .\scripts\train_ames.py
     Cela génère `models/ames_rf_mapie.joblib`.
5. Lancer l'API :

   - uvicorn app.main:app --reload --port 8000

Démarrer le frontend

1. Se placer dans le dossier frontend (ou dossier client où se trouve package.json) :
   - cd frontend
     (si le front est à la racine, adaptez le chemin)
2. Installer les dépendances :
   - npm install
     (ou yarn)
3. Lancer l'app en mode développement :
   - npm run dev
     ou
   - npm start
4. S'assurer que le front appelle l'API backend :
   - API backend attend : http://127.0.0.1:8000
   - Si nécessaire, modifier la base URL dans la config/front-end pour pointer vers ce endpoint.

Remarques rapides

- Le backend accepte des instances JSON et renvoie pour chaque instance : { prediction, lower, upper }.
- Envoyer les valeurs manquantes comme `null` (JSON) pour que l'imputation côté pipeline les gère.
- En production, restreindre CORS et ajouter authentification / dockerisation.

Si tu veux, je te fournis un README plus détaillé (ajout d'exemples d'appels curl, Dockerfile, ou composant front React) — dis‑moi ce que tu préfères.
