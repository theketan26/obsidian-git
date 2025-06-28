1. Add URL pattern in url.py of a application
2. path ```(“<endpoint>”, <method>, name=”<name of the endpoint>”)```
	1. endpoint server like ```<domain>/<app name>/<provided endpoint>```
	2. method is the function runs on hitting the end point
		1. param is a request
		2. response is a HttpResponse
		3. generally defined in app/views.py
	3. name is the name of end point for admin reference