## What is Carol Connect, aka 2C

Carol Connect is a generic extractor to allow new Carol related projects to quickly extract data from databases supported by different SGBD technologies and send them to Carol's staging area.

2C connects the the database and looks at the changes done to individual tables to know what is to send and uploads the data.

The main objective is to reduce cost of integration for solutions that do not have a native integration or support the TOTVS Standard Message communication protocol.

### How?

2c works by appending a new trigger (bear with me) to the selected tables to integrate them to a queue. The queue will be consumed by the service and used the fetch the data back in the original table and send it to Carol's staging area.

The trigger is extremelly simple, always composed with this instructions:
````
    when inserting or updating a record:
        insert the primary key values and table name in the queue
````
Simple, huh?

The queue itself will contain the table name, the primary key fields values and the status of that specific record syncronization. Once a record is sucessfully sent, it's deleted from the queue.



- build
    - describre process, tools etc
- configuration
    - config files
- deploy
- auth
- add a new integration
    - db types 
        - params
    - error scenarios
- check connection health
    - event log
- add a new table
    - configure simple table
    - configure identifier
    - configure conditional
- enable/disable pause/unpause