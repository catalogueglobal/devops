**REQUIREMENTS:**
- node 6.9+
- npm 3+
- java 8
- maven 3.3+
- docker 1.12 +
- docker-compose

**CATALOGUE SERVER**

`git checkout catalogue/datatools-server branch dfactory`

`mvn clean package`

`sh docker-build.sh`

**CATALOGUE METADATA**

`git checkout catalogue/metadata branch master`

`mvn clean package`

`sh docker_build.sh`

**CATALOGUE UI**

`git checkout catalogue/catalogue_ui branch integration`

`npm i -g @angular/cli@1.0.0-beta.32.3`

`npm i`

`ng build`

`sh docker_build.sh`

**BOOSTRAPING WITH DOCKER**

`git checkout catalogue/devops`

copy datatools-server/conf/env.yml.tmp to datatools-server/conf/env.yml and fill the values with your own setup (Auth0)

`docker-compose up -d`

- The app is then accessible at the url : `http://localhost:1081/`
- No GTFS files
- Upload on local file storage (S3 storage disabled)

**ALTERNATIVE**

in datatools-server : 

`java -jar target/dt-<commit>.jar configurations/local/env.yml configurations/local/server.yml`

the app should be accessible on `localhost:4000`

in metadata : 

`java -jar target/metadata.jar`

the app should be accessible on localhost:4400

in catalogue_ui :

`ng serve`

the app should be accessible on localhost:4200

**WARNINGS**

You might need to mkdir the datatools data directories (found in server.yml) to avoid server errors when uploading GTFS files

- mapdb
- gtfs
- editor
- geojson
