## jpl-validator

Application that validates the main YAML-based configuration file from the v2
series of the
[indigo-dc/jenkins-pipeline-library](https://github.com/indigo-dc/jenkins-pipeline-library).

The validation uses a [JSON schema](src/main/resources/schema.json) (Draft 7).

### Usage

#### Directly with gradlew
```
$ ./gradlew run --args='.sqa/config.yml'
```

#### Building & running (fat)JAR

```
$ ./gradlew fatJar
$ java -jar ./build/libs/jpl-validator-2.0.0.jar .sqa/config.yml
```

#### Through Docker (via Google's Jib)

##### Just build the Docker image

```
$ ./gradlew jibDockerBuild
$ docker run --rm -v $PWD:/jpl eoscsynergy/jpl-validator:2.0.0 /jpl/.sqa/config.yml
```

##### Build & push Docker image

```
# Set first JPL_USERNAME and JPL_PASSWORD variables pointing to the Docker registry's username and password
$ ./gradlew jib
$ docker run --rm -v $PWD:/jpl eoscsynergy/jpl-validator:2.0.0 /jpl/.sqa/config.yml
```
