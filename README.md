# jenkins-with-docker

Sets up a container with jenkins, docker and docker-compose installed.

## Usage

To run the container, do the following:

    $ docker run -d -p 8080:8080  -v /var/run/docker.sock:/var/run/docker.sock \
    andyyoung01/jenkins-with-docker
    
Your jenkins instance is now available by going to http://your-hostip:8080 .

### Persistent Configuration

By default, JENKINS_HOME is set to /var/jenkins.  The best way to persist or import configuration is to have a separate data volume for /var/jenkins. You can use data-volume like this:

    $ docker run --name jenkins-data andyyoung01/jenkins-with-docker echo "Jenkins Data Container"
    $ docker run -d -p 8080:8080  -v /var/run/docker.sock:/var/run/docker.sock \
    --volumes-from jenkins-data andyyoung01/jenkins-with-docker


