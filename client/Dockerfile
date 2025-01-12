# Étape 1 : Utiliser une image de base légère
FROM node:lts-alpine

RUN mkdir -p /user/src/app
# Étape 2 : Définir le répertoire de travail dans le conteneur
WORKDIR /user/src/app

# Étape 3 : Copier les fichiers package.json et package-lock.json
COPY package*.json ./

# Étape 4 : Installer les dépendances
RUN npm install

# Étape 5 : Copier le reste des fichiers du client
COPY . /user/src/app/

# Étape 6 : Construire l'application React
RUN npm run build

# Étape 7 : Installer un serveur HTTP léger pour servir l'application
RUN npm install -g serve

# Étape 8 : Exposer le port 3000
EXPOSE 3000

# Étape 9 : Démarrer le serveur pour servir les fichiers de build
CMD ["serve", "-s", "build"]
