# mathematics-library-cornell-edu-migrate

Post D8 migration import of CSV file into math site

Move the Excel spreadsheet into Filemaker to create the UID field

* UID is md5 hash of Author,Title,Place,Publisher,Date,Cornell Holdings
* GetContainerAttribute (string ; "MD5" )
* delete all existing records, then import xlsx file
* import worksheet 'CollectedWorks'
* don't import UID or Subset fields
* aboout 1084 records
* delete first record - Field names and generated UID
* delete records at the end with no Author

Export from Filemaker as CSV file

* export to file collected_works_fm_csv.csv
* manually add field list to first record
* field order: UID,Author,Title,Place,Publisher,Date,CornellHoldings,BIBID,OCLCID,WorkID
* Unicode (UTF-8)
* be sure _line endings_ in the csv file are _unix_ (LF only) not windows (CRLF) or mac (CR)
  * Textwrangler can set the line endings

Import collected-works-csv.yml file as a Configuration Type 'Migration'

* pull the site down into Kalabox
* /admin/config/development/configuration/single/import
* configuration type Migration
* paste in the yml file contents

If you get an error like this:
>  An entity with this machine name already exists but the import did not specify a UUID.

* go to /admin/config/development/configuration/single/export
* Configuration type Migration
* The Configuration name popup will list all the migrations ids in parens after the configuration name
  * (see the id: line in collected-works-csv.yml)
* Change the id: line in collected-works-csv.yml so it's unique and Import again

Place the csv file where Drupal can see it

* ~/Kalabox/mathematicslibrarycornelledu/code/mathematics-site

Drupal command to import configuration

* kbox drush migrate-import collected_works10

All commands in migrate_tools: (migrate_tools)
>
    migrate-fields-sourc  List the fields available for mapping in a source.
    migrate-import (mi)   Perform one or more migration processes.
    migrate-messages      View any messages associated with a migration.
    migrate-reset-status  Reset a active migration's status to idle.
    migrate-rollback      Rollback one or more migrations.
    migrate-status (ms)   List all migrations with current status.
    migrate-stop (mst)    Stop an active migration operation.

Another method
`
terminus drush mathematicslibrarycornelledu.dev migrate-import collected_works_1
`

** MAKE SURE THE CSV FILES HAVE UNIX LINE ENDINGS **

** MAKE SURE NONE OF THE LINES IN THE CSV FILE ARE EMPTY **
