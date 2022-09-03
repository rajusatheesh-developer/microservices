# microservices
- Data Hiding is best practice when working with Microservices
- Create Database credentials per service based 
- What are your thoughts on fetching relevant data to my service and caching it - then listening to events for creation/update/delete so at call-time a service doesn't   have to make as many inter-service calls to its dependencies?
- Shared Data Patterns
   - Database as Enpoint
   - Database views
   - Change Data Capture - capture a change : Debezium and Kafka , Oracle Golden Gate
- Migration order
   - Data First or Code first 
   - Data First 
      - Split shared data
      - For Distributed txns we can use Two phase commit but has drawbacks
   - Code First
     - Extract part of logic into separate service 
     - What ablout Data Hiding?
        Extract via Monolith using API then Move Data specific to that service
        May occur circular dependency
        
- Referential integrity with Monolith database
  - Join Performance
  - Enforce referential integrity
  - Joins explicit
- Referential integrity across multiple databases
   - Lacks
     - Join Performance
     - Enforce referential integrity
     - Joins explicit
   - How to ensure referential integrity ?
     - SOFT delete - Update Status column as NOT_AVAILABLE OR DELETED
     - COPY Data
        - Maintain multiple copies of data 
        - what about source data changes ? Need to update all copies and copying takes time so performance measured on how to impl copy data
      - CHECK for use before Delete - Not preferred
         - Locks required
      - Cascading Deletes using Events        
# Q&A
- how do we handle the referential integrity constraints in the Monolithic DB when we moving out the invoicing db?
   - JOINS at Service Tier
   - We will call endoint to get referential data 
   - We need to talk to stakeholders on acceptable Latency when we are making service level calls
- Is it always worth building feature-parity split out into microservices as opposed to building new functionality as new services? Just knowing limited resource for all the work alongside maintaining the monolith ?
- How to handle reporting needs where data from multiple microservices are needed? E.g sales in the last year. Does the Finance have to fetch all products from Catalog by Id (for details) or is there a better way of handling that? I saw cases where the list of Ids is so long that it does not fit as a query string.
