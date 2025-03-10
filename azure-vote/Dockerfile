# Ouvrez le Dockerfile dans votre éditeur et changez la dernière ligne :
FROM python:3.9-slim

WORKDIR /app

# Installation des dépendances système
RUN apt-get update && \
    apt-get install -y curl && \
    rm -rf /var/lib/apt/lists/*

# Copie des fichiers de l'application
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

# Configuration du healthcheck
HEALTHCHECK --interval=30s --timeout=3s --start-period=5s --retries=3 \
    CMD curl -f http://localhost:80/ || exit 1

# Exposition du port 80 (interne)
EXPOSE 80

# Commande de démarrage (changement ici)
CMD ["python", "main.py"]