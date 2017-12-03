## Overview 
We have two indpendent projects:
* deepak-client 
* deepak-server
Both are built using spring boot framework. Maven is used as a build tool.


## Running Server and Client 

Clone the repository.
* `git clone <repository-url>`

#### Starting the server
1. Go into directory `deepak-sever`
2. Build the prject and make fresh jar file: 
   * `mvn clean install`
   * To skip tests use `mvn clean install -Dmaven.test.skip=true -DskipTests -Dmaven.test.failure.ignore=true`
3. Run the server on port 9091 (or any available port.)
   * `java -jar target/deepak-server-0.1.0.jar --server.port=9091`

#### Starting the client
1. Go into directory `deepak-client`
2. Build the prject and make fresh jar file: 
   * `mvn clean install`
   * To skip tests use `mvn clean install -Dmaven.test.skip=true -DskipTests -Dmaven.test.failure.ignore=true`
3. Run the server on port 9090 (or any available port.)
   * `java -jar target/deepak-client-0.1.0.jar --server.port=9090`

## Invoking Requests
1. Connect to server and store data in client 
   * http://localhost:9090/fetchAndStore/9091
   * Use request type = GET (Rpeat to keep adding new records to client db.)
   * Result: Fetches a new record from sever and saves the same into client database.

2. GET request: 
   * http://localhost:9090/getAddressById/1
   * Use request type = GET
   * Result: Gets the record mathing with suplied ID. 


#### Use postman like tool to make other requests.
3. UPDATE request:
   * localhost:9090/updateAddress
   * Pass the full address object JSON in body (Raw and Select JSON in postman)
   * Use request type = PUT
   * Result: Updates the specified record in client db.

4. DELETE request:
   * localhost:9090/deteAddress
   * Pass the address ID in body
   * Use request type = DELETE
   * Result: Deletes the specified record in client db.

5. SAVE request (direct save on client)
   * localhost:9090/updateAddress
   * Pass the full address object JSON in body (raw and select JSON)
   * Use request type = POST


## Future Improvements
   1. Add security. 
   2. Add logging.
   3. More specfic error messages in error handling.
   4. Use properties files for error handling. For custom errors.
   5. Let client pass full server address or make it confgurable. eg. through prperties file.
   6. Add conversion for date field in Address - make it human readable espeically when using in UI.
   7. Add type of address for resuability. Eg. Home Address, Office Address.
   8. Add server tests: task said we could have used mock sever so have not added any server side tests.


## Troubleshooting
1. mvn: command not found?
  - Please install maven. I won't tell how. :simple_smile
2. Cannot clone? Git says host not found?
  - Please check your proxy settings.
  - You may need to export these variables into environment:
    ```
    export HTTP_PROXY="<your url here>"
    export HTTPS_PROXY=$HTTP_PROXY
    export http_proxy=$HTTP_PROXY
    export https_proxy=$HTTP_PROXY
    export NO_PROXY=“<your url here>”
    export no_proxy=$NO_PROXY
    ```
2. Maven build error?
  - This might be because of maven failing to find the JAVA_HOME.
  - Please export your JAVA_HOME if maven cannot find it. `eport JAVA_HOME=<your java home>`
3. Cannot download maven dependenices?
  - Please check the proxy settings for maven
  - You can add proxies for maven in your  settings file `~/.m2/settings.xml`.
  - You may not need username and password in proxy elements.
  ```
  <proxy>
    <id>http8080</id>
    <active>true</active>
    <protocol>http</protocol>
    <host>your host here</host>
    <port>8080</port>
    <username></username>
    <password></password>
    <nonProxyHosts>your host|localhost|home</nonProxyHosts>
  </proxy>
  ```
  
