# Deploiement-de-Mongodb-et-Mongo-Express-UI-sur-Kubernetes-
Déployer Mongodb et y accéder depuis l'interface utilisateur Mongo-Express sur Kubernetes. 

## Mongo Express
Interface d'administration Web MongoDB écrite avec Node.js, Express et Bootstrap3 


## Caractéristiques
--------

* Se connecte à plusieurs bases de données 
* Afficher/ajouter/supprimer des bases de données
* Afficher/ajouter/renommer/supprimer des collections
* Afficher/ajouter/mettre à jour/supprimer des documents
* Permet d'afficher des ressources audio/vidéo/image en ligne dans la vue de la collection
* Les objets imbriqués et/ou volumineux sont pliables pour une vue d'ensemble facile
* Chargement asynchrone à la demande des propriétés de documents volumineux (> 100 Ko par défaut) pour garder la vue de la collection rapide 
* Prise en charge de GridFS - ajouter/obtenir/supprimer des fichiers incroyablement volumineux 
* Utiliser les types de données BSON dans les documents 
* Mobile / Responsive - Bootstrap 3 fonctionne passablement sur les petits écrans lorsque vous êtes dans l'impasse 
* Connectez-vous et authentifiez-vous à des bases de données individuelles
* Permet l'authentification administrateur pour afficher toutes les bases de données 
* Permet de classer les bases de données en Liste noire/liste blanche

## URL de service externe 
----------
<img src="Screenshots/external-service-url.png" title="External Service URL from Minikube">

## Captures d'écran
-----------
Page d'accueil | Vue de la base de données | Vue Collection | Mise à jour d'un document
--- | --- | --- | ---
![Alt text](Screenshots/mongo-express-home-page.png?raw=true "Title")| ![Alt text](Screenshots/mongodb-collections.png?raw=true "Title") | ![Alt text](Screenshots/mongodb-collection-view.png?raw=true "Title") | ![Alt text](Screenshots/Editing%20the%20documents.png?raw=true "Title")

## Variables d'environnement
-----------
Vous pouvez utiliser ce qui suit [Variables d'environnement](https://docs.docker.com/reference/run/#env-environment-variables) pour modifier la configuration du conteneur : 

|Name                              | Default         | Description|
|----------------------------------|-----------------|------------|
|`ME_CONFIG_MONGODB_SERVER`        |`mongo` or `localhost`| MongoDB host name or IP address. The default is `localhost` in the config file <br/> and `mongo` in the docker image. If it is a replica set, use a comma delimited list of the host names.|
|`ME_CONFIG_MONGODB_PORT`          | `27017`         | MongoDB port.|
|`ME_CONFIG_MONGODB_URL`           | `mongodb://admin:pass@localhost:27017/db?ssl=false`||
|`ME_CONFIG_MONGODB_ENABLE_ADMIN`  | `false`         | Enable administrator access. Send strings: `"true"` or `"false"`.|
|`ME_CONFIG_MONGODB_ADMINUSERNAME` | ` `             | Administrator username.|
|`ME_CONFIG_MONGODB_ADMINPASSWORD` | ` `             | Administrator password.|
|`ME_CONFIG_MONGODB_AUTH_DATABASE` | `db`            | Database name (only needed if `ENABLE_ADMIN` is `"false"`).|
|`ME_CONFIG_MONGODB_AUTH_USERNAME` | `admin`         | Database username (only needed if `ENABLE_ADMIN` is `"false"`).|
|`ME_CONFIG_MONGODB_AUTH_PASSWORD` | `pass`          | Database password (only needed if `ENABLE_ADMIN` is `"false"`).|
|`ME_CONFIG_SITE_BASEURL`          | `/`             | Set the express baseUrl to ease mounting at a subdirectory. Remember to include a leading and trailing slash.|
|`ME_CONFIG_SITE_COOKIESECRET`     | `cookiesecret`  | String used by [cookie-parser middleware](https://www.npmjs.com/package) to sign cookies.|
|`ME_CONFIG_SITE_SESSIONSECRET`    | `sessionsecret` | String used to sign the session ID cookie by [express-session middleware](https://www.npmjs.com/package/express-session).|
|`ME_CONFIG_BASICAUTH_USERNAME`    | ``              | mongo-express web login name. Sending an empty string will disable basic authentication.|
|`ME_CONFIG_BASICAUTH_PASSWORD`    | ``              | mongo-express web login password.|
|`ME_CONFIG_REQUEST_SIZE`          | `100kb`         | Used to configure maximum mongo update payload size. CRUD operations above this size|will fail due to restrictions in [body-parser](https://www.npmjs.com/package/body-parser).|
|`ME_CONFIG_OPTIONS_EDITORTHEME`   | `rubyblue`      | Web editor color theme, [more here](http://codemirror.net/demo/theme.html).|
|`ME_CONFIG_OPTIONS_READONLY`      | `false`         | if readOnly is true, components of writing are not visible.|
|`ME_CONFIG_SITE_SSL_ENABLED`      | `false`         | Enable SSL.|
|`ME_CONFIG_MONGODB_SSLVALIDATE`   | `true`          | Validate mongod server certificate against CA|
|`ME_CONFIG_SITE_SSL_CRT_PATH`     | ` `             | SSL certificate file.|
|`ME_CONFIG_SITE_SSL_KEY_PATH`     | ` `             | SSL key file.|
|`ME_CONFIG_SITE_GRIDFS_ENABLED`   | `false`         | Enable gridFS to manage uploaded files.|
|`VCAP_APP_HOST`                   | `localhost`     | address that mongo-express will listen on for incoming connections.|
|`VCAP_APP_PORT`                   | `8081`          | port that mongo-express will run on.|
|`ME_CONFIG_MONGODB_CA_FILE`       | ``              | CA certificate File|
|`ME_CONFIG_BASICAUTH_USERNAME_FILE`     | ``        | File version of ME_CONFIG_BASICAUTH_USERNAME|
|`ME_CONFIG_BASICAUTH_PASSWORD_FILE`     | ``        | File version of ME_CONFIG_BASICAUTH_PASSWORD|
|`ME_CONFIG_MONGODB_ADMINUSERNAME_FILE`  | ``        | File version of ME_CONFIG_MONGODB_ADMINUSERNAME|
|`ME_CONFIG_MONGODB_ADMINPASSWORD_FILE`  | ``        | File version of ME_CONFIG_MONGODB_ADMINPASSWORD|
|`ME_CONFIG_MONGODB_AUTH_USERNAME_FILE`  | ``        | File version of ME_CONFIG_MONGODB_AUTH_USERNAME|
|`ME_CONFIG_MONGODB_AUTH_PASSWORD_FILE`  | ``        | File version of ME_CONFIG_MONGODB_AUTH_PASSWORD|
