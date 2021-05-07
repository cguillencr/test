# testing
This repository creates a jmeter image to execute performance testing inside the container then get the results in a folder on the local machine. The code is based on https://www.blazemeter.com/blog/make-use-of-docker-with-jmeter-learn-how and was modified to add all *.jmx inside the "Code" folder to be executed from the container. Also a Test.jmx was added as an example.

To run the case just execute the following lines inside the "code" folder

```
docker build -t "testing:jmeter" .
docker run -v <<PATH in your local machine>>/results:/results --name jmeter testing:jmeter <<Jmeter file and arguments>>
```
per example
```
docker build -t "testing:jmeter" .
docker run -v D:/jmeter_docker_example/results:/results --name jmeter testing:jmeter -n -t /Test.jmx -l /results/Test.jtl -e -o ../results/
```
Note that the arguments "-l /results/Test.jtl" and "-e -o ../results/" were added after "-n -t /Test.jmx" to generate a couple of reports that will be published in the "results" folder of your local machine

The image was pushed in https://hub.docker.com/r/cguillenmendez/testing if you prefer to work with that directly.