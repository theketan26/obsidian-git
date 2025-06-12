# The Pattern to follow
```
lib/
├── core/
│   ├── di/
│   │   └── service_locator.dart
│   ├── extensions/
│   │   ├── context_extensions.dart
│   │   └── string_extensnions.dart
│   ├── network/
│   │   ├── api_client.dart
│   │   ├── api_error.dart
│   │   ├── api_response.dart
│   │   └── http_methods.dart
│   ├── routes/
│   │   ├── app_router.dart
│   │   └── navigation_service.dart
│   ├── styles/
│   │   ├── app_colors.dart
│   │   ├── app_text_style.dart
│   │   ├── app_theme.dart
│   └── utils/
│       └── widgets/
│       └── constants/
│           ├── app_constant.dart
│           ├── app_images.dart
│           ├── app_strings.dart
│           ├── app_typedef.dart
│           ├── api_url.dart  
│           ├── app_routes.dart
│           ├── common_exports.dart
│           └── typedef.dart
├── features/
│   ├── <module-name>/
│   │   ├── data/
│   │   │   ├── models/
│   │   │   └── repositories/
│   │   ├── domain/
│   │   │   └── repositories/
│   │   └── presentation/
│   │       ├── provider/
│   │       ├── views/
│   │       └── widgets/
├── main.dart
└── myapp.dart
```


# Briefs
### Data
Data is the data related logics i.e. storing, fetching and manipulation from raw API data to presentation data.
Fetch data from client only, do not call API in data layer.
Methods are present in repositories, these repositories are abstracted in domain/repositories.
Types/Models are in models

### Domain
Domain is abstract for data, it contains all the abstract methods are will be used in data/repositories.
All classes/methods used in providers or view, will be from domain only.

### Presentation
Widgets that will be used directly in view, these will not be completely dumb and may have logic inside, all will be sent from parent, which will be view widget.
Views will be the widgets going to be used directly on router. These widgets are smart enough to communicate with providers only. No view will have logic from repository layer.
Providers are controllers for the views. It will control the user interactions and flow of data between view and domains.
### Network
All the API related methods and handles everything, error, response, client, urls.
#### Client
It will contain the main query and mutation methods, that will be imported from http methods based on the request method.
It will handle authentication, headers and request configs.
The urls will be imported from
If error received, forward to error.
Else, forward to response.
#### Error
It will handle the errors, if received by client.
#### HTTP Methods
It will contain the methods for GET, POST, PATCH, PUT and DELETE method API calls.


### Routes 
#### App router
It will contain the main router for the application that will be responsible for authentication and routing and dependency injection.
#### Navigation service 
It will have the method related to navigation, such as push, pop, and conditional push.


### Styles
This is the main source of the styles for the materials going to be used, such as scaffold, app-bar, bottom navigation, buttons, sheets, etc.
This will contain the color constants.
### Utils
#### Widgets
These will the generic widget that will be customized according to needs.
#### Constants
These will be the constants going to be used in the application.
### Service locator
These are the dependencies that will be injected in the views from routers
### Extensions
These are basically the extra methods for already existing classes, such as BuildContext and String.
#### Context extension
These are the common methods that are going to be used in multiple files.
#### String extension
These are the common string methods that are going to be used in multiple files.



### Flows
