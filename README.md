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
