# context_extension.dart
```
extension BuildContextExtensions on BuildContext {
  // Theme shortcuts
  ThemeData get theme => Theme.of(this);
  TextTheme get textTheme => Theme.of(this).textTheme;
  ColorScheme get colorScheme => Theme.of(this).colorScheme;
  
  // Screen size helpers
  double get screenWidth => MediaQuery.of(this).size.width;
  double get screenHeight => MediaQuery.of(this).size.height;
  
  // Navigation helpers
  void pop<T>([T? result]) => Navigator.of(this).pop(result);
  Future<T?> pushNamed<T>(String routeName) => 
      Navigator.of(this).pushNamed<T>(routeName);
      
  // Snackbar helper
  void showSnackBar(String message) {
    ScaffoldMessenger.of(this).showSnackBar(
      SnackBar(content: Text(message))
    );
  }
}
```

# Sample use case
```
import 'package:your_app/core/extensions/string_extensnions.dart';

void example() {
  // Validation
  final email = 'user@example.com';
  if (email.isValidEmail) {
    print('Valid email');
  }
  
  // Formatting
  final name = 'john doe';
  print(name.titleCase); // Outputs: "John Doe"
  
  // Truncation
  final longText = 'This is a very long text that needs to be truncated';
  print(longText.truncate(20)); // Outputs: "This is a very long..."
}
```