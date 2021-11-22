# JUNIT-Training
Training
Contents
Setting up REST API service on your local machine	1
API Specifications for “Generate Token” API	2
API Specifications for “View Account Details” API	2
API Specifications for “Update Account Details” API	2


Setting up REST API service on your local machine

In-case you wish to practice API scripting using these API’s then you can use below two methods.


1.	Download and install hoverfly (LINK)


Use below command to run hoverfly on win. You need to be in hoverfly folder (C:\hoverfly_bundle_windows_amd64) to run below command

hoverctl start --listen-on-host 0.0.0.0 webserver --import simulation_800_1000_2000.json


Make sure you have below file under hoverfly folder (C:\hoverfly_bundle_windows_amd64)
 

=======================================================================
2.	Pull the docker image from docker hub and run it on your local machine.

Use below command to run this REST API service on your local machine
docker run -it -p 8888:8888 -p 8500:8500 d752892/rest-api-demo
or
winpty docker run -it -p 8888:8888 -p 8500:8500 d752892/rest-api-demo


$ winpty docker run -it -p 8888:8888 -p 8500:8500 d752892/rest-api-demo
Unable to find image 'd752892/rest-api-demo:latest' locally
latest: Pulling from d752892/rest-api-demo
Digest: sha256:de41ff5c8dfcb0653fa9408150bd5091bce48e5ce5c3accb44a60fc7c386703e
Status: Downloaded newer image for d752892/rest-api-demo:latest
INFO[2020-07-13T07:18:14Z] Default proxy port has been overwritten       port=8500
INFO[2020-07-13T07:18:14Z] Default admin port has been overwritten       port=8888
INFO[2020-07-13T07:18:14Z] Listen on specific interface                  host=0.0.0.0
INFO[2020-07-13T07:18:14Z] Using memory backend
INFO[2020-07-13T07:18:14Z] payloads imported                             failed=0 successful=4 total=4
INFO[2020-07-13T07:18:14Z] Webserver prepared...                         Destination=. Mode=simulate WebserverPort=8500
INFO[2020-07-13T07:18:14Z] current proxy configuration                   destination=. mode=simulate port=8500
INFO[2020-07-13T07:18:14Z] serving proxy
INFO[2020-07-13T07:18:14Z] Admin interface is starting...                AdminPort=8888




API Specifications for “Generate Token” API
Method: POST
Endpoint : http://localhost:8500/generate/token
Mandatory Headers:
Content-Type: application/json
 
Query parameters:
scope : accounts
client_id : username
client_secret: password 
grant_type: client_credentials



API Specifications for “View Account Details” API

Method: GET
Endpoint: http://localhost:8500/account/details/{AccountID}
Mandatory Headers:
Content-Type: application/json
Authorization: valid token


API Specifications for “Update Account Details” API

Method: POST
 
Endpoint :http://localhost:8500/update/account/details
Mandatory Headers:
Content-Type: application/json
Authorization: {token}
 
Request Body
{
	"AccountId": "111",
	"UpdatedBy": "Perf Test Coach",
	"Mobile": "1111111111"
}
 


