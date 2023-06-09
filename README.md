# AI4Users Sandbox Server
This is the repo for the AI4Users Sandbox. It's written in Python 3 with Flask for serving HTTP requests, and has Docker set up for easy deployment to any server.

## System architecture and dataflow
This diagram shows the dataflow of the three main functionalities of this system. <br/>
Module calls are mainly omitted from the diagram except from retrieving a model from scikit-learn. <br/>
For further inspection, documentation is provided in their respective files. <br/> <br/>
![diagram](img/system_architecture.png?raw=true)

## Making sick leave estimate request
By looking at src/index.py, we can see the POST request to `/process_data` handles sick leave requests. Example body:
```json
{
	"region": "Agder",
	"age": "16-19",
	"disorder": "pregnancy disorders",
	"gender": "female"
}
```

## Running the server
The server has been containerized via the use of Docker and Docker compose for both ease of use and reliability. In order to run the server, simply run:
```sh
docker-compose up
```
This will build and start the dockerized Python Flask server, and it should then be ready to accept HTTP POST requests on `/process_data`. If you wish to start the docker instance in the background, you can add the `-d` tag (detached) to docker-compose so that it becomes: `docker-compose up -d`.

### Stopping the server
Stopping the server is done via the `docker-compose down` command.

## Testing
cd to `src/tests/` and run `pytest` to perform tests.
