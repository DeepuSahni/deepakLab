## We have two indpendent projects:
* deepak-client
* deepak-server

Both are built using spring boot framework. Maven is used as a build tool.


## Running Server and Client 

Clone the repository
#### Start the server:
1. Go into directory deepak-sever
2. Make a fresh jar file:
   * `mvn clean install`
3. Run the server on port 9091 (or any available port.)
   * `java -jar target/deepak-server-0.1.0.jar --server.port=9091`

### Starting the client:
1. Go into directory deepak-client
2. Make a fresh jar file:
   * `mvn clean install`
3. Run the server on port 9090 (or any available port.)
   * `java -jar target/deepak-client-0.1.0.jar --server.port=9090`

## Invoking Requests:
1. Connect to server and store data in client 
   * http://localhost:9090/fetchAndStore/9091
   * Use request type = GET (Rpeat to keep adding new records to client db.)
   * Result: Fetches a new record from sever and saves the same into client database.

2. GET request: 
   * http://localhost:9090/getAddressById/1
   * Use request type = GET
   * Result: Gets the record mathing with suplied ID. 


#### Use postman like tool to make other requests.
3. Update request:
   * localhost:9090/updateAddress
   * Pass the full address object JSON in body (Raw and Select JSON in postman)
   * Use request type = PUT
   * Result: Updates the specified record in client db.

4. Delete request:
   * localhost:9090/deteAddress
   * Pass the address ID in body
   * Use request type = DELETE
   * Result: Deletes the specified record in client db.

5. Save request (direct save on client)
   * localhost:9090/updateAddress
   * Pass the full address object JSON in body (raw and select JSON)
   * Use request type = POST


## Future Improvements:
   1. Add security. 
   2. Add logging.
   3. More specfic error messages in error handling.
   4. Use properties files for error handling. For custom errors.
   5. Let client pass full server address or make it confgurable. eg. through prperties file.
   6. Add conversion for date field in Address - make it human readable espeically when using in UI.
   7. Add type of address for resuability. Eg. Home Address, Office Address.
   8. Add server tests: task said we could have used mock sever so have not added any server side tests.
