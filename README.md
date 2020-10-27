## GLog

This simple class library was created as part of a larger, ongoing project.  This is certainly not the most comprehensive or bulletproof Logging library available, but it works and suits my needs.

It allows the user to log events to a file with some formatting, including DateTime timestamps, custom event level names, and multiline indentation.

Usage is simple: add it to your project and then:
```
using Honeypox.GLog
GLog logger = new GLog
{
    LogPath = "my_log.log";
}
logger.Warning("This is a warning message");
logger.Error("Error message");
```

You can log string, string[], List\<string\>, or Exceptions.  If you try anything else, it will attempt to convert it to a string.

Public GLog Properties:
```
  string LogPath         // which file to log to
  bool TimestampEntries  // whether to include the DateTime in the log entry
  bool IndentEntries     // whether to indent lines after the first to align vertically after the DateTime timestamp and Level
  bool TabulateEntries   // whether to add a tab (4 spaces) to lines after the first
  string DateFormat      // custom DateTime format, defaults to "MM/dd/yyyy hh:mm:ss tt"
```
Public GLog Methods:
```
  Custom()               // These all generate a log entry using the appropriate Level notation
  Debug()
  Warning()
  Error()
  Critical()
```
GLog.Level Properties:
```
  string Warning         // string for warning notation, default "WARN"
  string Error           // string for error notation, default "ERRO"
  string Critical        // string for critical notation, default "CRIT"
  string Debug           // string for debug notation, default "DEBU"
  string Custom          // string for custom notation, default "CUST"
```

An example log generated while testing with default settings looks like this:
```
ERRO 10/27/2020 01:52:02 PM: Error Message!
CRIT 10/27/2020 01:52:02 PM: The following JSON string is long and has many parts:
    {
      "recipeId": 0,
      "webId": 12345,
      "rating": 5.5,
      "website": "a.recipe.com",
      "url": "a.recipe.com/carrotanans",
      "ingredients": [
        {
          "ingredientId": 0,
          "recipeId": 0,
          "quantity": 1,
          "description": "Carrot, chopped",
          "recipeSection": "Base:",
          "unit": "Cup"
        },
        {
          "ingredientId": 1,
          "recipeId": 0,
          "quantity": 1,
          "description": "Banana, sliced",
          "recipeSection": "Base:",
          "unit": "Tbsp"
        }
      ]
    }
DEBU 10/27/2020 01:52:02 PM: This string array has
    multiple
    lines
ERRO 10/27/2020 01:52:02 PM: This is an error message.
INTR 10/27/2020 01:52:02 PM: Attempted to write to log, but string was empty.
INTR 10/27/2020 01:52:02 PM: Attempted to write to log, but string was empty.
INTR 10/27/2020 01:52:02 PM: Attempted to write to log, but string was empty.
CUST 10/27/2020 01:52:02 PM: Custom message!
NEWC 10/27/2020 01:52:02 PM: Changed the custom message notation!
```

Also allows you to clear a log with `ClearLog()`
