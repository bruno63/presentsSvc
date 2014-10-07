# presentsBE2

This project is a blueprint backend application (storing presents) built using [baucis](https://github.com/wprl/baucis).
It consists of
- a MongoDB database (defined by a Mongoose schema) that is populated with some test data
- a Node.js/Express server application that is generated by Baucis based on the Mongoose schema.
- a REST interface 'presents' that serves the backend application (also generated by Baucis)
- a browsable REST API documentation generated by Swagger

## Prerequisites:
- Node.js / npm
- MongoDB needs to run on default port 27017.

## Assumptions:
- application will be served on port 3333
Application and MongoDB ports can be configured in config/config.js.

## Installation:
    git clone https://github.com/DigiKMU/presentsBE2.git
    cd presentsBE2
    npm install
    node app

## Configuration
- config/config.js      configuration parameters and the Mongoose schema
- test/testdata.json    test data in JSON format

## Usage:
When the server is running, the application can be called via HTTP requests, e.g:

    http://localhost:3333/api/presents
    http://localhost:3333/api/presents?conditions={ "from": "bruno" }
    http://localhost:3333/api/presents?conditions={ "comment": { "$regex": "K" } }
    http://localhost:3333/api/presents?select=_id
    http://localhost:3333/api/presents/<_id>

Check out POST, PUT, HEAD, and DELETE requests as well…

This can be done by 
- manually calling the above URL's from within a browser
- command line tools such as curl
- programmatically, e.g. from within a JavaScript application or any other web client calling the REST interface
- test scripts

# REST API documentation

Using Swagger, a browsable description of the REST API can be generated.

## Installation
download the [swagger-ui](https://github.com/wordnik/swagger-ui) client.

    git clone git@github.com:wordnik/swagger-ui.git
    open swagger-ui/dist/index.html

call the API:

    http://localhost:3333/api/api-docs
    http://localhost:3333/api/api-docs/presents

# TODO
- integrate Passport (authorization / access control)
- support versioning (controller.versions)
- more tests (unit and e2e)
- support multiple environments
- automatic deployment to OpenShift
- generation of frontend skeleton

