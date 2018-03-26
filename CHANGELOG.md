# Changelog
All notable changes to this project will be documented in this file.

## 2.9.1 - 2018-03-26
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
