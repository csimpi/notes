# JSON
How to get rid annoying encoding issues...

### Case 1
I just got an issue with saving an angularjs object to a MySQL database.

- Client sent me CSV files for the database (UTF-8)
- I imported it to the database
- I was able to show the data from the database without any issue
- I was able to convert the object to JSON string and convert it back to object before storing them in the database

**Issues**

1. MySQL error during INSERT
2. If I saved the JSON string to the database then I wanted to get it back, I wasn't able to convert the JSON string back to array, I was getting JSON syntax errors.

**Solutions**

1. MySQL error during INSERT

Don't forget encode the `'` and `"` characters to htmelntity or something like that.

`htmlentities($str,ENT_QUOTES)` will encode `'` and `"` characters both.

2. Invalid JSON error during decode
Remove invalid UTF-8 characters, and convert all whitespace characters to regular space
```
$row['room_desc'] = preg_replace('#[^\x20-\x7E]#',' ',$row['room_desc']);
$row['room_desc'] = preg_replace('/(\s*\n){2}/',' ',$row['room_desc']);
```
