pipeline {
  agent any

  stages {
    stage ('one') {
steps {
  sh """yum install httpd -y
  systemctl start httpd
  git clone 
  cp /root/.jenkins/workspace/test/R2/index.html /var/www/html/
  cd
  chmod -R 777 /var/www/html/
  systemctl restart httpd"""
}
      
    }
  }
}
