# Useful Curl Stuff

#### Curl url with a specific user agent
```
curl -v -L --user-agent "Mozilla/5.0 (iPhone; U; CPU iPhone OS 4_0 like Mac OS X; en-us) AppleWebKit/532.9 (KHTML, like Gecko) Version/4.0.5 Mobile/8A293 Safari/6531.22.7" <url>
```

#### Curl url with a specific user agent
```
curl -v -L --user-agent "Mozilla/5.0 (compatible; MSIE 9.0; Windows Phone OS 7.5; Trident/5.0; IEMobile/9.0; SAMSUNG; SGH-i917)" <url>
```

#### Curl a response into a file
```
sudo curl -v -L <url> > response.txt
```

#### Get a response with json headers
```
curl -v -i -H 'Accept: application/json' <url> > response.json
```

#### Download a file
```
curl <url>.tgz > ~/Downloads/file.tgz
```

#### Extract the file
```
cd ~/Downloads
tar -zxvf file.tgz
```

#### Test a rest api via curl

#### Get
```
curl -i -X GET http://localhost:3000/users
```

```
curl -i -X GET http://localhost:3000/users/5069b47
```

#### Delete
```
curl -i -X DELETE http://localhost:3000/users/5069b47
```

#### Add
```
curl -i -X POST -H 'Content-Type: application/json' -d '{"name": "Robocop", "year": "1982"}' http://localhost:3000/users
```

#### Modify
```
curl -i -X PUT -H 'Content-Type: application/json' -d '{"name": "Murphy", "year": "1984"}' http://localhost:3000/users/5069b47
```

#### Change referer 
```
curl --referer <referer_url> <url>
```

#### Get a number of files from a location
```
curl -O -L <url>{1.sfx,2.rar,3.rar}
```

#### Bust cache
```
curl -X GET -I -H "Cache-Control: no-cache" localhost/assets/stylesheets/application.css
```