#  Platform Data Base Backup And Restoration

The SCAVA Platform use a Mongo database to store data related to analysed projects (project data, analyse process data and  measurements collected durnig the analysis process). A backup of this data can be  performed using the default Mongo backup service.


## SCAVA Platform Data Model

The SCAVA Data mode is composed of several data bases. Each of this databases must be backuped individually 

| Database        | Description   |
| ------------- | -----|
| scava     | The scava databases contains information related to Analysed Projects including the list of all repository related to this project  |
| scava-analysis |  The scava-analysis databases contains information related to analysis process. For each analysed project, this database contains information related to the defined analysed tasks and information related the execution of this anlaysis tasks |
| {AnalysedProjectName}| For each analysed project, the SCAVA Platform store the result of the analyse (collected measurements) a is a separate database. The Name of this database is the shortName of the project. The  shortName of a project cab be retrive using the REST API exposed by the platform ( http:/{platform url}:{platform port}/project)|

## Backup Process

The Mongo installation package(windows and linux)  provide the **mongodump** service whic allow to create a database dump

> mongodump --gzip --archive=<ARCHIVE_NAME> --db <DB_NAME> --port <DB_PORT>


Example :
```
mongodump --gzip --archive=scava.20180906.gz --db scava --port 27018                   // project database
mongodump --gzip --archive=scava-analysis.20180906.gz --db scava-analysis --port 27018 // analysis process database
mongodump --gzip --archive=QualityGuard.20180906.gz --db QualityGuard --port 27018     // QualityGuard project database
```

## Restoration Process

The Mongo installation package( windows and linux)  provide the **mongorestore** service which allow to restore a database dump

> mongorestore --drop --gzip --archive=Activemq.20181203.gz 

Example :
```
mongorestore --drop --gzip --archive=scava.20181203.gz           // project database
mongorestore --drop --gzip --archive=scava-analysis.20181203.gz  // analysis process database
mongorestore --drop --gzip --archive=QualityGuard.20181203.gz    // QualityGuard project database
```

