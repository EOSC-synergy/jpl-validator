## jpl-validator

Application that validates the main YAML-based configuration file from the v2
series of the
[indigo-dc/jenkins-pipeline-library](https://github.com/indigo-dc/jenkins-pipeline-library).

<img src="https://github.com/EOSC-synergy/service-qa-baseline/blob/master/content/images/logo-SYNERGY.png" height="80">

## Institutions owning the result
<p float="left">
    <img src="https://github.com/EOSC-synergy/service-qa-baseline/blob/master/content/images/logo-LIP.png" height="80">
    <img src="https://github.com/EOSC-synergy/service-qa-baseline/blob/master/content/images/logo-csic.png" height="80">
    <img src="https://github.com/EOSC-synergy/service-qa-baseline/blob/master/content/images/logo-UPV.png" height="80">
</p>

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

```
$ ./gradlew jibDockerBuild
$ docker run --rm -v $PWD:/jpl eoscsynergy/jpl-validator:2.0.0 /jpl/.sqa/config.yml
```
