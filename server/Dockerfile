# Étape 1 : Utiliser une image de base légère
FROM node:lts-alpine

RUN mkdir -p /user/src/app
# Étape 2 : Définir le répertoire de travail dans le conteneur
WORKDIR /user/src/app

# Étape 3 : Copier les fichiers package.json et package-lock.json
COPY package*.json /user/src/app

# Étape 4 : Installer les dépendances
RUN npm install

# Étape 5 : Copier le reste des fichiers de l'application
COPY . /user/src/app

# Étape 6 : Exposer le port utilisé par votre serveur
EXPOSE 9000


# Étape 8 : Lancer l'application
CMD ["npm", "start"]
