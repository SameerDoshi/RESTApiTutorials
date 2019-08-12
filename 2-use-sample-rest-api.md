#Sample REST API Use
## NO Code
Let's first do something with no code
[https://reqres.in/](https://reqres.in/) contains a sample api and if you scroll down you can see buttons that simulate various calls.

Click each button and take a look at the request that's generated.

Everything is standarized.  There's so many methods but they basicly all match up to what you learned in the last page.  That's cool right!?    Now remember that almost all APIs written follow the same form!  If you know one you know 90% of how to use any REST api!!!

## Code Sample
Ok let's write some super simple code.

Open up PowerShell (Linux/MacUsers- either install [PowerShell](https://docs.microsoft.com/en-us/powershell/scripting/install/installing-powershell-core-on-macos) or move to the next section and use [Postman](https://www.getpostman.com/downloads/))

Let's create some variables so we don't have to retyepe the same things again and again.
```powershell
$uri='https://reqres.in/api/'
```

Now let's do our simple GET request
```powershell
Invoke-RestMethod -Method Get -Uri $uri+'users'
```

Boom! the result is a bunch of users.  
If we wanted to get a big more advanced we could assign that to a variable and iterate over the data
This will give us just the usernames:
```powershell
$ResultsOfGetUsers=Invoke-RestMethod -Method Get -Uri $uri+'users'
foreach($user in $ResultsOfGetUsers.data){$user.name}
```

Anyway this isn't a PowerShell tutorial but you can see we can do some cool stuff once we grab teh data.
Let's go create a user.  To do this we'll convert the JavaScrip Object Notation (JSON) on our sample API page to PSON (PowerShell Object Notation)- this will save us from typing:
```powershell
$myUser=ConvertFrom-JSON '
 {
     "name": "morpheus",
     "job": "leader",
     "id": "334",
     "createdAt": "2019-08-12T14:50:31.115Z"
 }';

Invoke-RestMethod -Method Post -Uri $uri+'users' -Body $myUser
```

BOOM! You've created a user!
Let's edit that user:
```powershell
$updatedUser=ConvertFrom-Json '{
  "name": "morpheus",
  "job": "zion resident"
}'

Invoke-RestMethod -Method Put -Uri $uri+'users/334' -Body $updatedUser
```

YEASH! You updated the user you created.  We'll do a delete and call it a day:
```powershell
Invoke-RestMethod -Method Delete -Uri $uri+'users/334'
```


## Summary
You did it.  You wrote some very simple REST calls, and you did some pretty amazing things without having to read through documenation.  You can use the same simple commands on all kinds of rest apis.  The only wrinkle we haven't talked about is auth.  But it's simple too and we'll talk about that next.