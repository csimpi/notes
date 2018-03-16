# Laravel First Impressions

## User add/ Add new db column (name)
Laravel won't store everything that we are sending, so we have to add name column to the fillable array.
`app/User.php`

```
protected $fillable = [
    'username', 'email', 'password','name'
];
```

`app/Http/Controllers/UserController.php`

Getting the posted data ($request) then make a User object with the posted data, then save it to the database
```
$userData = $request->all();
$userData['username'] = !empty($userData['username']) ? $userData['username'] : $userData['email'];
$user = new User($userData);

if (!$user->save()) {
    abort(500, 'Could not save user.');
}
```


## Eloquent
https://hackernoon.com/eloquent-relationships-cheat-sheet-5155498c209
