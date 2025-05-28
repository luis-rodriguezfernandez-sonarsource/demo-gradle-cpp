# SonarCloud Gradle C++ Example

## What?

This is a simple example of a C++ project using Gradle, which is analyzed by SonarCloud.

This project has been created following [Building C++ Applications Sample](https://docs.gradle.org/current/samples/sample_building_cpp_applications.html) 

## How?

Analyzing C or C++ code requires - in addition to the source code - the configuration that is used to build the code. See 
more at [Alternative ways of configuring c and cpp analysis](https://www.sonarsource.com/blog/alternative-way-to-configure-c-and-cpp-analysis/)
This configuration is provided by the `compile_commands.json` file. Gradle does not provide a task to generate this 
compilation database, that's why we need a third party tool like [bear](https://github.com/rizsotto/Bear).

Below you can find the steps to install `bear`, generate the `compile_commands.json` file and run the SonarCloud analysis.

```shell

sudo apt install bear

mkdir bw-output

bear --output bw-output/compile_commands.json -- gradle clean build

sonar-scanner -Dsonar.organization=luis-rodriguezfernandez-sonarsource -Dsonar.projectKey=demo-gradle-cpp -Dsonar.sources=app/src -Dsonar.cfamily.compile-commands=bw-output/compile_commands.json -Dsonar.host.url=https://sonarcloud.io -Dsonar.token=xxxx
```
