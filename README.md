# android-build-docker
Dockerfile to set up a Jenkins slave for building Android apps.

## Example to run a build slave.
Launch command:
```bash
docker run --rm -a stderr -a stdin -a stdout -i -e JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64 -v /path/to/Android/Sdk:/sdk:ro,Z -v /path/to/jenkins:/data/jenkins:rw,Z -e ANDROID_HOME=/sdk android-build:8 java -jar /data/jenkins/slave.jar
```
You need to manually fetch the slave.jar from http://yourserver:port/jnlpJars/slave.jar and place in /path/to/jenkins on the container host.
Note that you may also need to specify --dns depending on your network set-up.
Remote root directory in this case is /data/jenkins.
You should also specify the same ```ANDROID_HOME``` and ```JAVA_HOME``` in the environment variables in node properties.
