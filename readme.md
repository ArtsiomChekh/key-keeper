# key-keeper

### Run app

#### Postgresql:
1) > key-keeper % docker-compose up

##### Ember server:
1) > key-keeper % sbt 
2) > sbt:key-keeper> run io.chekh.keykeeper.Application
   
##### Query keys table via psql:
1) > key-keeper % docker exec -it key-keeper-db-1 psql -U docker
2) > \c board;
3) > select * from keys;

### Run tests
1) > key-keeper % sbt
2) > sbt:key-keeper> test

### HTTP requests.

##### Health routes:
* http GET localhost:8080/api/health

##### Key routes:
(using HTTPie)
* **Create**: http POST localhost:8080/api/keys/create < src/test/resources/payloads/json/gitkeyinfo.json
* **Get**: http GET localhost:8080/api/keys/(3b75de13-4290-4003-8daf-bda30e7dfea8)       
* **Lookup**: http GET localhost:8080/api/keys/lookup/(git)
* **Update**: http PUT localhost:8080/api/keys/(3b75de13-4290-4003-8daf-bda30e7dfea8) < src/test/resources/payloads/json/updatedkeyinfo.json
* **Delete**: http DELETE localhost:8080/api/keys/(3b75de13-4290-4003-8daf-bda30e7dfea8)   

* **Export to csv**: http GET localhost:8080/api/keys/export/csv > src/test/resources/payloads/csv/exported_keys.csv
* **Import from csv**: http POST localhost:8080/api/keys/import < src/test/resources/payloads/csv/imported_keys.csv
