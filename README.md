OSM Client
-----------
The OSM Client is used to simulate all the device (web, tablet, tv, ...) and all the environments (staging, production, QA, ...) in order to easily emulate the request for the OSM API without the need to generate the MD5 Hash.

DEPLOY
---------
### Prepare release
* Increase api version, 2.x.x in osm-client.gemspec
* Update changelog file `ChangeLog`

  ```
Version 2.4.2 Released on 2042/01/01

    * MEDIABO-273: .......
    * Bugfix:      .......
  ```

### Deploy to arkena-gems.herokuapp.com

```
./deploy.sh 2.4.2
```

BROWSER VERSION
---------
### Build the js
```
rake build
```

CONSOLE VERSION
---------
### Require the gem
```
require 'osm_client'
```

### Create a new Client
```
new_client = OsmClient.new(device, environment, debug)
	device(String)      = the name of the device u wanna to emulate. e.g: "web", "lg-tv" ...
	environment(String) = the name of the environment u wanna to emulate. e.g: "staging", "production" ...
	debug(Boolean)      = true if u wanna to put the debug ON

e.g: new_client = OsmClient.new('web', 'production', false)
```

### Authorize your client
```
new_client.client_authorize # This give you an access_id and an access_secret
new_client.user_authorize(login, password)
	login(String) 		= Your login
	password(String)	= Your password
```

TEST
--------
```
bundle exec rake spec
```