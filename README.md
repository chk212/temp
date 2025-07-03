# Bot Discord de gestion de temps de charge

## Fonctionnalités
- `/start` : Démarre le chronomètre de charge
- `/stop` : Arrête le chronomètre et enregistre la session dans un fichier Excel
- `/stats` : Affiche la moyenne de temps de charge et le nombre de charges par mois
- `/history` : Affiche l'historique complet des charges
- **Affichage web** : Visualise l'historique des charges dans un tableau web dynamique

## Installation
1. Clone ce dépôt
2. Installe les dépendances :
   ```bash
   pip install -r requirements.txt
   ```
3. Crée un bot Discord et récupère son token : https://discord.com/developers/applications
4. Ajoute le token dans un fichier `.env` :
   ```env
   DISCORD_TOKEN=ton_token_ici
   ```
5. Génère le fichier Excel si besoin :
   ```bash
   python -c "import openpyxl; wb = openpyxl.Workbook(); ws = wb.active; ws.append(['UserID', 'Date', 'Durée (minutes)']); wb.save('charge_log.xlsx')"
   ```
6. Lance le bot (qui démarre aussi l'API web) :
   ```bash
   python bot.py
   ```

## Affichage web de l'historique

1. **Lance un serveur web local** dans le dossier du projet :
   ```bash
   python -m http.server 8000
   ```
2. **Ouvre ton navigateur** et va à l'adresse :
   [http://localhost:8000/index.html](http://localhost:8000/index.html)

Tu verras un tableau dynamique avec l'historique des charges issu du fichier Excel.

## API Flask
- L'API est disponible sur : `http://localhost:5000/charges`
- Elle retourne le contenu du fichier Excel au format JSON.

## Utilisation Discord
Invite le bot sur ton serveur et utilise les commandes slash `/start`, `/stop`, `/stats`, `/history`.