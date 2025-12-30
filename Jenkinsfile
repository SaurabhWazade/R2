pipeline {
agent {
label {
label "dev"
}
}
tools {
maven "apache-maven-3.9.12"
}

environment {
project_url = "https://github.com/Shantanumajan6/SprintBootService-1.git"
b&d_url = ""
}

stages {
stage('build') {
steps {
sh """rm -rf *
git clone ${project_url}
cd SprintBootService-1
mvn clean package
cd /mnt/test
cp -r sprintBootService1-1/project/SpringBootExecutableJarFileDemo-0.0.1-SNAPSHOT.jar .
"""
}

}
stage('B&D') {
steps {
sh "cd /mnt/test
git clone ${b&d_url}
docker build -t saurabhwazade/project1:1.0 .
docker push saurabhwazade/project1:1.0
kubectl apply -f deploy.yaml
kubectl apply -f service.yaml"
}
}
}
}
