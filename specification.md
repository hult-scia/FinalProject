# Final Project Specification



Your final project is half your grade. For simplicity let us say it is 50 points. The project should have 2 repositories. 

1. A library like `wikiapp` to hit openai using its API, and get a response. Well tested, linted, formatted, documented, types added and tested with `mypy`, and built and uploaded to testpypi. Call it `genailib_rd` where you replace `rd` by your initials. The idea here is that testpypi needs different names for you to upload, so you need to distinguish your libraries. Make sure that this library has, like `wikiapp`, validation of returned values from the openai API using `pydantic`, the ability to choose different models, and the ability to get the openai key from the environment or a `.env` file. Also make sure you have a command-line app like the one we developed in the `wikiapp` repository
2. A server like `wikiserver` or the server in `uistuff` which is written in `flask` and handles communication with openai, users, conversations, and chatd in a conversation. The functionality in `uistuff` should be a good guide. You may use a `wikiserver` like multi-page interface or a `uistuff` like "single-page application(SPA)". Either way make sure the code is tested (you are hitting your own flask server after all), linted, formatted, documented, typed. To make it deployed and run on docker you can use any of the the dockerfile methods described in the `todoapprd` repository, but make sure the database file and configurations come from outside the docker container: in other words, keep the container generic. For testing, read this [part](https://flask.palletsprojects.com/en/3.0.x/testing/) of the flask documentation and the links within this page, especially the link to the testing of their example app `flaskr`. Make sure you have a command line application that talks to openai, that is a useful feature in itself.

Then a rough rubric is this:

1. 26 points for good software development practices: testing..both unit-testing using pytest and mocks, and end-to end testing, linting, formatting, types, docs, building/deploying. Roughly 13 each for each library.
2. 4 points for a good CLI application in the library package.
3. It is ok if the javascript parts of your app are not tested. But make sure the app is responsive by testing at different widths and on different devices. A decent looking and functional user interface is worth 15 points. The user interface must provide:
   1. login
   2. registration
   3. users
   4. conversations
   5. chats within conversations
   6. all chats and conversations automatically saved
   7. the last 3 (you can change this number) back-and forths must be sent to the model to provide good context, unless there is an option in the API to have openai remember these for you.
   8. optionally let the user change the model
4. 5 points are reserved for any additional nice stuff you do, like number 8 above!



## Resources

1. The `wikiapp` library is a good source for software development practices for libraries
2. I linked above information on how to test flask
3. the `uistuff` repo if a good source for SPA code
4. the `wikiserver` repo is a good resource for multi-page server stuff
5. the `todoapprd` repo is a good resource for deployment/docker ideas
6. It is important to have a good `.gitignore` file. I added one in this repo. It is identical to the one in `wikiapp` and it ignores the `.env` file.
7. I'll add more here.

