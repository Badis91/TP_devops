Service de Location de Voitures
Ce projet propose un service de location de voitures développé avec Node.js. Il peut être exécuté localement ou déployé dans un environnement Docker ou Kubernetes avec Istio.

Fonctionnalités principales
API REST
GET toutes les voitures disponibles.

GET les détails d’une voiture via son numéro d’immatriculation.

PUT pour modifier les dates de réservation d’un véhicule.

Interface utilisateur
Visualiser les voitures ainsi que leur disponibilité.

Réserver un véhicule pour une période donnée.

Réinitialiser le statut de réservation d’un véhicule.

Déploiement
Conteneurisation Docker : le service peut être packagé dans une image Docker.

Orchestration Kubernetes : prêt à être déployé sur un cluster Kubernetes avec prise en charge d’Istio.

Technologies requises
Node.js

Docker (optionnel)

Kubernetes (optionnel)

Istio (optionnel)

Mise en route

1. Clonage du dépôt
bash
Copier
Modifier
git clone https://github.com/Badis91/Tp_devops

3. Installation des dépendances
bash
Copier
Modifier
cd app
npm install

5. Lancement du service
Exécution locale
bash
Copier
Modifier
npm start
Accédez ensuite à l’interface web à l’adresse :
http://localhost:4000

Utilisation avec Docker
Création de l’image Docker :

bash
Copier
Modifier
docker build -t rentalservice .
Démarrage du conteneur :

bash
Copier
Modifier
docker run -p 4000:4000 rentalservice
Ouvrez votre navigateur sur :
http://localhost:4000

Déploiement sur Kubernetes
Vérifiez que kubectl et Istio sont installés.

Lancez le déploiement :

bash
Copier
Modifier
kubectl create deployment rentalservice --image=tonybynmp4/rentalservice:1
ou avec le fichier de configuration :

bash
Copier
Modifier
kubectl apply -f deployment.yaml
Configurez l’accès via Istio :

bash
Copier
Modifier
kubectl -n istio-system port-forward deployment/istio-ingressgateway 31380:8080
Accédez au service via :
http://localhost:31380

Détails des routes API

Méthode	Endpoint	Description
PUT	/api/cars/:numberPlate	Met à jour la période de location d’un véhicule.
GET	/api/cars/:numberPlate	Donne les informations d’une voiture spécifique.
GET	/api/cars	Liste toutes les voitures.
