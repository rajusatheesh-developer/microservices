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
        
# Q&A
-how do we handle the referential integrity constraints in the Monolithic DB when we moving out the invoicing db?
