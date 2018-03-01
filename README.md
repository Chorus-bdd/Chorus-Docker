# Chorus-Docker

Builds a Docker image which can be used to run the Chorus interpreter

https://hub.docker.com/r/chorusbdd/chorus-interpreter/

This can either be used standalone (to save installing java and Chorus on the local OS), or run alongside other services using docker-compose

This image contains the Java runtime and Chorus interpreter dependencies - everything needed to run Chorus!

### Invoking Chorus 

A good way to invoke Chorus is to 

1. Start a Chorus container as a daemon, mounting a directory of feature files you wish to run as a volume
2. Run the tests, by executing the `chorus` command within the running container

This can be done with the following commands:

* `docker run -v /path/to/features:/features -d --name chorus-interpreter chorusbdd/chorus-interpreter`
* `docker exec chorus-interpreter chorus -c -f /features`

This command will run chorus in 'console' mode (-c) for pretty output, and execute the features mounted under /features (-f)


### Adding to the Chorus classpath

To add custom step implementations in Java, you need a way to add handler classes and other resources to the Chorus classpath

Chorus will look for these under the paths `/choruslibs` and `/chorusclasses`, so you can:

1. Mount a volume containing jars into the container at `/choruslibs`, or
2. Mount a volume containing classes and other resources at `/chorusclasses`

If you wish to use Chorus built in SQL handler you will need to make JDBC driver jars available under /choruslibs




