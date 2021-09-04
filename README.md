# how to install sonarQube in your local machine

### 1. First you need install docker-desktop ( most simple way )



### 2. Then You need to copy `sonar-install.yml` in this repo 
* you can change file name or new the file and copy paste by yourself

### 3. use `sonar-install.yml` run your docker 

* in the `sonar-install.yml` place, open command line
* run `docker-compose -f sonar-install.yml up` in your command line
* you should see your docker like that
* ![alt text](https://github.com/liyo1242/sonarQube-setting/blob/master/test.png?raw=true)

### (ERROR YOU MAY GET)

* sonarQube is stop and say `max virtual memory areas vm.max_map_count [65530] is too low, increase to at least [262144] `

- how to fix: Type following two line in your command line
```
wsl -d docker-desktop
echo 262144 >> /proc/sys/vm/max_map_count
```
* restart your docker image
