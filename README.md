# phaidra-agents
Agents using Phaidra's agent framework

# apim-harvester

## Install

```bash
  cpanm Daemon::Control
  cpanm Net::Stomp
  cpanm XML::XML2JSON
  cpanm JSON::XS
```

## Config (/etc/phaidra.yml)

```yml
apimharvester:
 stomp_host: 'localhost'
 stomp_port: 61613
 stomp_user: 'not used at present'
 stomp_password: 'not used at present'
 mongo_host: 'mongohost'
 mongo_user: 'user'
 mongo_password: 'pass'
 mongo_port: 27017
 mongo_db:  'instancedb'
 mongo_collection: 'apim' 
 update_topic: 'fedora.apim.update'
 access_topic: 'fedora.apim.access'
```

Create capped mongodb collection...
```
db.createCollection( "apim", { capped: true, size: 1000000 } )
```

...or convert a created one to capped.
```
db.runCommand({"convertToCapped": "apim", size: 1000000});
```


## Run

```bash
./apim-hooks-daemon.pl start
```

