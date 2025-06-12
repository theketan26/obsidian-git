```
// Example implementation using get_it
final GetIt serviceLocator = GetIt.instance;

void setupServiceLocator() {
  // Register singletons
  serviceLocator.registerSingleton<ApiClient>(ApiClient());
  serviceLocator.registerSingleton<UserRepository>(UserRepositoryImpl());
  
  // Register lazySingletons
  serviceLocator.registerLazySingleton<AuthService>(() => AuthServiceImpl());
  
  // Register factories
  serviceLocator.registerFactory<HomeViewModel>(() => HomeViewModel());
}
```