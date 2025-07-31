# Atomicity test cases

- use @Transactional annotation in JPA set up of tables related tables which store a business state shared among them.
- E.g. Case of Change of Address of a Student.
- Existing Address should be soft deleted and deassociated and the new address should be flagged as primary address.
- There are dml actions perfomed on address objects of same entity.
- The transaction should be successful only when both actions are successful.

# Consistency test cases

- Create an Entity
- Create objects of this entity
- Try to change any constraints of this entity
- The actions should fail
- Trace the error rootcause to generate from ORM or Database level
- The failure level suggest the layer which asserts consistency

# Isolation

- Changes to one entity object has no impact on other objects
- assert constraint failure when unique key violation is tried

# Durability

- Database starts
- Note a reference state at start
- Perform transaction
- Note a reference state post transaction
- Stop Database
- Start database again
- Note the reference of same object again
- assert the state matches post transaction performed.

# test database connection change when transation is in progress
- connection is establised
- transaction begins
- execution in progress
- ...
- Connection closes / network snapped etc
- assert that commit is not called in the process and no changes in database state is performed.
