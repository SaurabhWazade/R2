pipeline {

agent {
label {
label "built-in"
}
}
stages {
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
