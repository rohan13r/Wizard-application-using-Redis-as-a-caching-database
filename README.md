# Wizard-application-using-Redis-as-a-caching-database
Entities involved
Two main entities are involved
MasterHouse (master_houses)
Wizard (wizards)
Wizards have a many-to-one relationship with MasterHouse
Example:
Harry Potter (wizard) belongs to Gryffindor (masterHouse)
Ron Weasley (wizard) belongs to Gryffindor (masterHouse)
Hermione Granger (wizard) belongs to Gryffindor (masterHouse)
Griffindor (masterHouse) has Harry Potter, Ron Weasly and Hermione Granger (wizards)
Caching Flow
The house id is used as the key and the list of wizards belonging to that particular house are kept as the value in redis DB (key-value store)
The key is removed from the cache when a new wizard is added/updated/removed to/from that house
When the API is hit again, the updated list value is added to the cache and the process is repeated
Addition to that the API to retreive wizard by #id is also cached and goes through the above mentioned process as well where the wizard's pkey is used as a key to store the corresponding DTO value
Main classes/files
Service classes where caching is used
MasterHouseService
WizardService
.sql migration files
Flyway scripts
Redis config classes
Link
Technologies used
Java-15
Spring-boot
PostgreSQL
Flyway
Redis
Open-API(Swagger)
Lombok
