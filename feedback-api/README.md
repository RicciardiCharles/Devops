## Setting up for local development
To start the application you need to have [dotnet core 2](https://dotnet.microsoft.com/download/dotnet-core/2.2) installed in your computer.
After that make sure that you are in the root folder of feedback-api and execute the command:
```
$ dotnet run
```

This will create the database file in ./feedback-api/Database/Feedback.db where feedbacks will be stored. The database directory is defined in the file ./feedback-api/appsettings.json and can be overridden by the environment variable DATABASE_DIR.

#### Verify Local Feedback-api 

Add a feedback by executing the command below:

```
$ curl -i -X POST http://localhost:5020/feedback \
              -H "Content-type: application/json" \
              -d "{'sentence': 'I like', 'polarity': 0, 'correct': false}"
```

And get the feedbacks by executing:

```
$ curl -X GET http://localhost:5020/feedback
```


## Building the Docker Container

```
$ docker build -t localregistry.lc:30500/feedback-api .
```

## Creating the database

If you want to make changes to the model, you need to create a new migration and re-start the application.
To create a new migration execute:

```
$ dotnet ef migrations add $MIGRATION_NAME
```

## Building the Docker Container

```
$ docker build -t localregistry.lc:30500/feedback-api .
```

## Running the Docker Container

```
$ docker run -it -p 5020:80 --name feedback \
    -v ${PWD}/Database:/usr/db \
    -e DATABASE_DIR=/usr/db \
       localregistry.lc:30500/feedback-api
```

Hint: In `cmd` replace ${PWD} with %cd% -> both of these represent the current directory.