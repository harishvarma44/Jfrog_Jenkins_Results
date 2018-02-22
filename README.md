#Jenkins Project Name
Jfrog_PlugGit_Deploy_Versioning
#SCM
https://github.com/harishvarma44/Jfrog.git
#Versioning
Enable Artifactory release management
#Artifactory SErver
Resolve artifacts from Artifactory
Artifactory server 
192.168.58.201:8081/artifactory
#ROOT POM
maven-example/pom.xml
#POST STEPS
Run regardless of build
#pre steps
Exec shell
#POST-BUILD ACTIONS
DEploy artifacts to artifactory
#Git Publisher
Push build if BUild suceeds.   
