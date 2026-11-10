# Incident atelier 4

- Symptome : l'API repond sur /health mais toute connexion a la base depuis api echoue (Connection refused).
- Configuration effective : DB_HOST=localhost dans le conteneur api.
- Ecart : on attendait DB_HOST=db, le nom du service sur le reseau Compose.
- Hypothese : localhost designe le conteneur api lui-meme, pas db. Verifie : gethostbyname('db') reussit, connect(localhost,5432) est refuse.
- Correction : DB_HOST=db, puis docker compose up -d --force-recreate api.
