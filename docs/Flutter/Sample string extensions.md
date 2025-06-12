```
extension StringExtensions on String {
  // Validation helpers
  bool get isValidEmail => 
      RegExp(r'^[\w-\.]+@([\w-]+\.)+[\w-]{2,4}$').hasMatch(this);
  
  bool get isValidPassword => length >= 8;
  
  // Formatting helpers
  String get capitalized => 
      this.isNotEmpty ? '${this[0].toUpperCase()}${this.substring(1)}' : this;
      
  String get titleCase => 
      this.split(' ').map((word) => word.capitalized).join(' ');
      
  // Utility methods
  String truncate(int maxLength) => 
      this.length > maxLength 
          ? '${this.substring(0, maxLength)}...' 
          : this;
}
```