__1. Make Folder and file: app/Helpers/helpers.php__

__2. Register The helper to the composer.json__

```
  "autoload": {
          "classmap": [
              ...
          ],
          "psr-4": {
              "App\\": "app/"
          },
          "files": [
              "app/Helpers/helpers.php" // <---- ADD THIS
          ]
      },
      
```

__3. Run__

```
  composer dump-autoload
```
