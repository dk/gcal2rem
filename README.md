Google Calendar to remind format
================================

This reads your google calendar and dumps a remind(1) text file.

Installation
------------

Install prerequisites with this

```
   cpan API::Google::GCal DateTime::Format::RFC3339 JSON::XS
```

Then run `goauth` on your localhost. It will ask for client id and secret id.
These have to be created by yourself; follow the url goauth prints, to create
OAuth credentials, then go to localhost:3001 to create the API key for
gcal2rem. A config.json file will be created such as this:

```
{
   "gapi" : {
      "client_id" : ".....apps.googleusercontent.com",
      "client_secret" : "...",
      "tokens" : {
         "dmitry.karasik@gmail.com" : {
            "access_token" : "...",
            "refresh_token" : "...",
         }
      }
   }
}
```

Operation
---------

1) add call to gcal2rem in your crontab: `gcal2rem -c .../config.json -o /home/you/.remind/gcal`
2) add `INCLUDE /home/you/.remind/gcal` 

The remind file will look like this:

```
REM 12 Aug +3 %a whole day event
REM 20 Aug +3 %a 14:30 specific time event
```

