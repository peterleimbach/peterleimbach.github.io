# adding-password-for Node-RED

Adding password for users in Node-RED is fairly simple.

There is a small tool in the container by which you can create hashs for passwords.

Theses hashs can be assigned to a user in the settings.js file which is located in the data directory.

## creating the hash

Attach to the running container e.g. with portainer UI.

``` sh
node-red admin hash-pw
```

Your are getting asked for the password and it wil generate the hash for the password.

## adding the hash to settings.js

Add this hash in the settings.js file under "AdminAuth" which you need to uncomment.
You can change the user name too if you want.

``` js
     76     adminAuth: {
     77         type: "credentials",
     78         users: [{
     79             username: "admin",
     80             password: "theMagicHash",
     81             permissions: "*"
     82         }]
     83     },
```