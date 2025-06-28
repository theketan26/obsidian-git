1. Add the application in installed application in settings.py
	`<app name>.apps.<capitalized app name>Config`
2. Create method `<capitalized app name>Config` in `<app name>/apps`
3. Example method: ```
	class ProcessConfig(AppConfig):
	    default_auto_field = 'django.db.models.BigAutoField'
	    name = 'process'```
4. Create name Modal in