# SonarqubeUpgrade from 7.2 to 7.9.6

#Sonarqube requirements
    Server with minimum 2GB/1 vcpu capacity

    PostgreSQL version 9.3 or greater.
    
     OpenJDK 11 or JRE 11
      
     All sonarquber process should run as a non-root sonar user.
     
# Pre upgrade steps

    Needs to upgrade the Java 1.8 to Java 11 open jdk on centos
    
    Refernece link : https://sysadminxpert.com/steps-to-upgrade-java-8-to-java-11-on-centos-7/
    
    You can set them dynamically for the current session by running the following commands as root:(other wise you will the get the error)
    
         sysctl -w vm.max_map_count=524288
         sysctl -w fs.file-max=131072
         ulimit -n 131072
         ulimit -u 8192
         
    Reference link https://docs.sonarqube.org/latest/requirements/requirements/#header-4
































Reference Links
https://devopscube.com/setup-and-configure-sonarqube-on-linux/
