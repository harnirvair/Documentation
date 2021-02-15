


 
# Commands
 List apps of heroku 

    heroku apps

To export data

	heroku pg:backups:capture -a APPNAME
    heroku pg:backups:download -a APPNAME

To get URL name of the backup

	heroku pg:backups:url

 List of backups 
		
	heroku pg:backups -a APPNAME

Deleting backup

	heroku pg:backups:delete b101 -a foo

Reset Database: from Heroku website
OR using command

	heroku pg:reset URL

To open postgres shell of Heroku, visit heroku website/database
and enter the command written there in cmd


Inorder to restore a local database to postgresql online Heroku

	heroku pg:psql -a timetable-nsut < mine.dump

 No need to migrate then





