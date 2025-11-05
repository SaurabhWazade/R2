pipeline {

agent {
label {
label "built-in"
}
}
tools {
maven "apache-maven-3.9.11"
}
stages {
stage ('git') {
steps {
sh "git clone https://github.com/SaurabhWazade/project.git"
}
}
stage ('maven') {
steps { 
dir ('project') {
sh "mvn clean package"
}
}
}
stage ('scp'){
steps {
   // Use Jenkins SSH credentials
                withCredentials([sshUserPrivateKey(credentialsId: 'ssh-key', 
                                                   keyFileVariable: 'SSH_KEY',
                                                   usernameVariable: 'SSH_USER')]) {
                    sh '''
                    scp -o StrictHostKeyChecking=no -i $SSH_KEY project/target/LoginWebApp.war \
                    $SSH_USER@172.31.12.110:/mnt/servers/apache-tomcat-10.1.48/webapps/
                    '''
}
}
}
}
}
