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
         
# Package preparation 

1. Download the 7.9.6 from sonarqube site 
   https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-7.9.6.zip
   
2.  Download and unzip the SonarQube distribution of your edition in a fresh directory, let's say $NEW_SONAR_HOME and stop the sonarqube

3. If you're using third-party plugins, Manually install plugins that are compatible with your version of SonarQube. Use the Plugin Version Matrix to ensure that the versions      you install are compatible with your server version. Simply copying plugins from the old server to the new is not recommended; incompatible or duplicate plugins could cause      startup errors. Analysis of all languages provided by your edition is available by default without plugins.

4.Update the contents of sonar.properties and wrapper.conf files (in $NEW_SONAR_HOME/conf) with the settings of the related files in the $OLD_SONAR_HOME/conf directory (web    
  server URL, database, ldap settings, etc.). Do not copy-paste the old files. No need to update anything for PostgreSQL 


5.Start your new SonarQube Server

6.Browse to http://yourSonarQubeServerURL/setup and follow the setup instructions. It will make you to upgrade the postgress DB ad start the sonarqube

7. Most of plugins  will come with sonarqube installation. If you wnat to install then you can install it from marketplace. Some plugins (jar files)we have to place it on $NEW_SONAR_HOME/extensions/plugin and restart the  sonar qube service








Reference Links
https://devopscube.com/setup-and-configure-sonarqube-on-linux/
https://docs.sonarqube.org/latest/setup/before-you-upgrade/
https://docs.sonarqube.org/7.9/setup/upgrading/
