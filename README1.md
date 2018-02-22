#Jenkins Project Name
Deploy_Mavenproj
#SCM
https://github.com/harishvarma44/Jfrog.git
#Versioning
Enable Artifactory release management
#Artifactory SErver
Resolve artifacts from Artifactory
Artifactory server 
192.168.58.201:8081/artifactory
#Build Exec shell
--------------------------------------------------------------------------------------------------------------------
#PUlling artifacts from artifactory script
# Artifactory location
server=http://192.168.58.201:8081/artifactory
repo=libs-snapshot-local

# Maven artifact location
name=multi1
name1=multi2
artifact=org/jfrog/test/$name
artifact1=org/jfrog/test/$name1
path=$server/$repo/$artifact
path1=$server/$repo/$artifact1
version=`curl -s $path/maven-metadata.xml | grep latest | sed "s/.*<latest>\([^<]*\)<\/latest>.*/\1/"`
version1=`curl -s $path/maven-metadata.xml | grep latest | sed "s/.*<latest>\([^<]*\)<\/latest>.*/\1/"`
build=`curl -s $path/$version/maven-metadata.xml | grep '<value>' | head -1 | sed "s/.*<value>\([^<]*\)<\/value>.*/\1/"`
build1=`curl -s $path1/$version1/maven-metadata.xml | grep '<value>' | head -1 | sed "s/.*<value>\([^<]*\)<\/value>.*/\1/"`
jar=$name-$build.jar
jar1=$name1-$build1.jar
url=$path/$version/$jar
url1=$path1/$version1/$jar1

# Download
echo $url
wget -q -N $url
echo $url1
wget -q -N $url1
#POST-BUILD ACTIONS
--------------------------------------------------------------------------------------------------------------------------
