```shell

sudo apt install bear

mkdir bw-output

bear --output bw-output/compile_commands.json -- gradle clean build

sonar-scanner -Dsonar.organization=luis-rodriguezfernandez-sonarsource -Dsonar.projectKey=demo-gradle-cpp -Dsonar.sources=app/src -Dsonar.cfamily.compile-commands=bw-output/compile_commands.json -Dsonar.host.url=https://sonarcloud.io -Dsonar.token=xxxx
```