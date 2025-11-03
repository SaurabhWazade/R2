pipeline {
  agent any

  stages {
    stage ('one') {
steps {
  sh """yum install httpd -y
  systemctl start httpd
  git clone https://github.com/SaurabhWazade/R2.git
  cp /root/.jenkins/jobs/test/R2/index.html /var/www/html/
  cd
  chmod -R 777 /var/www/html/
  systemctl restart httpd"""
}
      
    }
  }
}
