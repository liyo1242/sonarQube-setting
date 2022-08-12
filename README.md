# how to install sonarQube in your local machine

### 1. First you need install docker-desktop ( most simple way )

### 2. Then You need to copy `sonar-install.yml` in this repo 
* you can change file name or new the file and copy paste by yourself

### 3. use `sonar-install.yml` run your docker 

* in the `sonar-install.yml` place, open command line
* run `docker-compose -f sonar-install.yml up` in your command line

### 4. Pick one way to scan your code

* install ```sonarqube-scanner``` in you project devDependencies, and write a file in your project root folder, then run it with ```node```
  ```js
  // * .sonar/index.js
  const scanner = require('sonarqube-scanner')

  scanner(
    {
      serverUrl: 'http://localhost:9000',
      token: 'YOUR_SONAR_TOKEN',
      options: {
        'sonar.projectName': 'PROJECT_NAME',
        'sonar.sources': 'src',
      },
    },
    () => process.exit()
  )
  ```
  ```shell
  // * Or you can put this command in your package.json script section
  node .sonar/index.js
  ```
* Enter SonarQube System in ```localhost:9000```, click the **Add Project** button on upper right corner, and follow the tutorial

### (ERROR YOU MAY GET)

* sonarQube is stop and say `max virtual memory areas vm.max_map_count [65530] is too low, increase to at least [262144] `

- how to fix: Type following two line in your command line ()
```
wsl -d docker-desktop
echo 262144 >> /proc/sys/vm/max_map_count
```
**if you want to solve this problem forever, you can refer to this answer**
https://stackoverflow.com/questions/69214301/using-docker-desktop-for-windows-how-can-sysctl-parameters-be-configured-to-per
* restart your docker image

### Note
* After you run sonarqube for a while, you may find that your C drive fills up quickly because sonar only deletes log files older than 30 days by default
* You can see those log files in User/.sonarlint/work
