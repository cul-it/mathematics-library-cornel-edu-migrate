# mathematics-library-cornell-edu-migrate

Post D8 migration import of CSV file into math site

Move the Excel spreadsheet into Filemaker to create the UID field
  * UID is md5 hash of Author,Title,Place,Publisher,Date
  * GetContainerAttribute (string ; "MD5" )

Export from Filemaker as CSV file
  * manually add field list to first record

Import collected-works-csv.yml file as a Configuration Type 'Migration'
  * /admin/config/development/configuration/single/import
  * paste in the file contents

Place the csv file where Drupal can see it
  * ~/Kalabox/mathematicslibrarycornelledu/code/mathematics-site

Drupal command to import configuration
  * kbox drush migrate-import collected_works10

All commands in migrate_tools: (migrate_tools)
 migrate-fields-sourc  List the fields available for mapping in a source.
 migrate-import (mi)   Perform one or more migration processes.
 migrate-messages      View any messages associated with a migration.
 migrate-reset-status  Reset a active migration's status to idle.
 migrate-rollback      Rollback one or more migrations.
 migrate-status (ms)   List all migrations with current status.
 migrate-stop (mst)    Stop an active migration operation.
