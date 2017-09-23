#Client/Server Setup of a SpringBoot & Angular App

Spring developers recommend a Client/Server architecture for creating a SpringBoot / SPA application.
See: <https://spring.io/blog/2014/07/24/spring-framework-4-1-handling-static-web-resources>

* The server is a vanilla SpringBoot app.
* The client was created using the Yeoman generator: Gulp Angular

Using the frontend maven plugin, we can utilise powerful front-end build tools (gulp, bower, npm, etc..) as part of
the maven build process. The main thing to get out of this project is how the pom.xml files are setup between the root, client, and server. The client is able to kick off its gulp builds to inject depedencies, build sass css, and minify js & css into a dist folder which is then ready for the server module. The server is then able to build the war with all javascript assembled and optimized. 

Keeping the client & server split lets you use yeoman generators for the front-end where the build process can be very complicated.

##Setup
To build and run completely from maven (you may need maven 3.3+ installed):

1. Run ```mvn install``` in root of directory. This will kick off the front-end and back-end build process.
2. ```cd server``` then execute the command ```mvn spring-boot:run```.

Running the generated client separately for auto-reload involves:

1. Install [node.js](https://nodejs.org/en/)
2. ```npm install -g gulp bower```
3. From client folder,
    1. ```npm install```
    2. ```bower install```
    3. ```gulp serve```
