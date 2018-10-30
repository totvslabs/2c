# Changelog
All notable changes to this project will be documented in this file.

## 2.17.0 - 2018-10-30
### Added
- Payload files are now splitted if they are bigger than 8Mb.
- 2c on Oracle databases now support images payloads.
- Oracle Clob data type are now supported. 
- Oracle and SQL Server databases now use payload directory to send data to Carol.
- Number of tables found now is displayed in the entities configuration screen.
### Changed
- Updated oracle driver dependency to ojdbc8 18.3.
### Fixed
- Enter key now works on login screen.

## 2.16.0 - 2018-10-15
- 2c now warns if it is not the latest version released.

## 2.16.0-beta - 2018-10-09
### Added
- 2c can now specify schema name in Oracle databases.
- Triggers are now created with the conditional filter configured on table activation.

## 2.15.3 - 2018-10-01
### Fixed
- Date format on internal derby database.
### Changed
- MySQL databases use cursor queries to avoid memory overflow.
- MySQL queries now have a query timeout. Default: 1 hour.

## 2.15.2 - 2018-09-24
### Changed
- MySQL databases now use payload directory to send data to Carol.

## 2.15.1 - 2018-09-18
### Fixed
- Oracle trigger names was exceeding 30 characters.

## 2.15.0 - 2018-09-17
### Changed
- Initial load files for OpenEdge database are now gzipped.

## 2.15.0-RC2 - 2018-09-11
### Changed
- Initial load on OpenEdge databases will use a temporary directory instead the queue table.

## 2.15.0-RC - 2018-09-05
### Added
- Now intial timestamp can be setted.
### Fixed
- Bug on schema change.
- Openedge databases was getting wrong schema name.

## 2.15.0-beta2 - 2018-08-29
### Added
- Entities are now sorted to priorize lookup tables.

## 2.15.0-beta - 2018-08-24
### Added
- Support for image reducing before send them to Carol.
### Fixed
- Removed unnecessary record count on MySQL databases for initial load.
- Wrong data format on sync by timestamp.

## 2.15.0-alpha - 2018-08-16
### Added
- Support for OpenEdge databases.
- Option to select more then one table to enable/disable.
- Option to view only existing tables in Carol.

## 2.14.0 - 2018-08-10
### Fixed
- Wrong data type on SQL Server float type
### Changed
- Updated SQL Server driver depency to 7.0.0

## 2.14.0-Beta3 - 2018-08-09
### Added
- 2c config file validation.
### Fixed
- Fix schema name on sync by timestamp.
- Fix MySQL trigger for delete.
### Changed
- Change MySQL inital load to avoid select count.

## 2.14.0-Beta2 - 2018-08-01
### Fixed
- Column name case divergence on Postgresql databases.
- New fields in SQL Server databases were being ignored.
### BREAKING CHANGES
- Binary data is now sent as base64 type.

## 2.14.0-Beta - 2018-07-27
### Added
- Two new synchronization modes: Sync by timestamp field and Sync by recurrent resynchronization.
### Removed
- Removed unnecessary entity cache.

## 2.13.3 - 2018-07-24
### Changed
- Updated oracle driver dependency to ojdbc8 12.2.0.1.

## 2.13.2 - 2018-07-10
### Fixed
- Unnecessary insert in queue table when inclusions occur with soft delete in protheus databases.

## 2.13.1 - 2018-07-03
### Fixed
- Fixed detection of Oracle numeric data type.
- Reduced max batch size to 8Mb.
- Fixed Postgresql resync criteria filter.
- Fixed field cache retriever for uppercase databases.
- Fixed authentication title typo.

## 2.13.0 - 2018-06-26
### Added
- Now 2c have a resync feature. It compares local data with remote data and sends the difference. Need to set `enableReSync` option on `app.config.yml` file.
- Added an embedded derby database on 2c data folder.
### Changed
- Login for 2c is now optional. To enable, just set `enableLogin` option on `app.config.yml` file.
### Fixed
- Reduced payload size by avoiding sending null data.

## 2.12.3 - 2018-06-15
### Fixed
- Fix next batch query on Oracle databases.

## 2.12.2 - 2018-05-25
### Changed
- Disabled extra login for 2c.

## 2.12.1 - 2018-05-16
### Changed
- Automatic start is now default for windows service.
- Increased log messages related to record retrieval.

### Fixed
- NullPointerException when no schema is informed for MSQLServer.
- When a batch is larger than 10Mb and the table definition has not yet been synchronized, some parts of this batch are not processed.

## 2.12.0 - 2018-05-11
### Added
- Increase max batch size to 10mb.
- It is now necessary to log in with the same user used to access Carol in order to use the 2c interface.

## 2.11.1 - 2018-05-09
### Fixed
- Bug fix that occurs when all pk records fetched from queue are already deleted from the original data table.

## 2.11.0 - 2018-04-26
### Added
- Allow to edit the database connection changing: host, username, password, etc.

### Fixed
- Charset problem during payload compaction on windows platform.
- Reduced jar size by removing unnecessary files during the build phase.

## 2.10.2 - 2018-04-23
### Fixed
- Increase database timeout.
- Get pending count poor performance.
- MySQL was inserting duplicate records on queue.
- Access control on initial load when MySQL and Postgres databases.

## 2.10.1 - 2018-04-17
### Fixed
- Fix data order on Postgresql.
- Fix unnecessary queue reset when no data was found.
- Fix bug that make some entities to pause.
- Fix Yaml concurrent parse problem.

## 2.10.0 - 2018-04-02
### Added
- GZip compaction to payload sent to Carol.
- Informix database compatibility.

### Fixed
- Performance improvement on pending records search. 

## 2.9.2 - 2018-03-27
### Fixed
- Optimized oracle get pending count query.

## 2.9.1 - 2018-03-26
### Added
- Added mechanism to control the order of sending data.

## 2.9.0 - 2018-03-20
### Added
- Image data is now sent to Carol on Base64 encoding.
- Support for Totvs Protheus soft delete on SQL Server and Oracle databases.

## 2.8.8 - 2018-03-16
### Fixed
- Can't do initial load on SQL Server 2008, sql syntax error.

## 2.8.7 - 2018-03-13
### Fixed
- 2c queue table should not be listed at entity selection.
- MySQL error on databases with timestamp zero valued.
- Table definition cache refactoring. When more than one thread access a database conection, it mixes fields definition.

### Added
- Database access control to avoid to many record locks.

## 2.8.6 - 2018-03-08
### Fixed
- Queue query not respects batch size on MySQL and SQLServer databases.

## 2.8.5 - 2018-03-06
### Added
- New application parameter `ignoreTriggers`, when 2c will only do the initial load and read the queue table. The integrated application will feed the carol_3c_queue manually in this case.

## 2.8.4 - 2018-03-02
### Added
- MySQL Database support.

### Fixed
- Fix ISO-8601 date format on delete requests.
- Oracle wrong date format saved in 3c queue.
- SQL Server wrong date format saved in 3c queue.
- Avoid to more than one thread getting the same batch.

## 2.8.3 - 2018-02-27
### Fixed
- Oracle trigger creation bug when trigger name is bigger than 30 caracters.

## 2.8.2 - 2018-02-22
### Added
- Integration triggers validation.
- Queue table validation.

### Fixed
- Oracle trigger creation bug with pk with date fields.

## 2.8.1 - 2018-02-20
### Fixed
- Fix PostgreSQL bug.

## 2.8.0 - 2018-02-20
### Added
- Support deletion operation from DB side.
- Add a flag to control when 2C is still running the initial load.

### Fixed
- Fix PostgreSQL bug.

### Security
- Update dropwizard version to address security fixes.

### BREAKING CHANGES
- New trigger for deletion.
- New carol_3c_queue field op_type.

## 2.7.4 - 2018-02-19
### Added
- Allow to configure 2C as a service on Windows.

### Fixed
- Fix PostgreSQL bug.

## 2.7.3 - 2018-01-31
### Fixed
- Queue reset divided in small batches to avoid database lock.

## 2.7.2 - 2018-01-31
### Fixed
- Fix queue status bug.

## 2.7.1 - 2018-01-24
### Fixed
- Fix Carol API parameter name.

## 2.7.0 - 2018-01-24
### Fixed
- Initial load divided in small batches to avoid database lock.
- Change Carol API parameter `applicationId` to `connectorId` name.

The format is based on [Keep a Changelog](http://keepachangelog.com/en/1.0.0/) and this project adheres to [Semantic Versioning](http://semver.org/spec/v2.0.0.html).
