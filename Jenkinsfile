pipeline {
    agent {
        label "dev"
    }

    tools {
        maven "apache-maven-3.9.12"
    }

    environment {
        PROJECT_URL = "https://github.com/Shantanumajan6/SprintBootService-1.git"
        BD_URL      = "https://github.com/SaurabhWazade/for-main-project.git"
        IMAGE_NAME  = "saurabhwazade/project1:1.0"
    }

    stages {

        stage('Build Application') {
            steps {
                deleteDir()

                sh """
                git clone ${PROJECT_URL}
                cd SprintBootService-1
                mvn clean package
                """
            }
        }

        stage('Build & Deploy') {
            steps {
                sh """
                git clone ${BD_URL}
                cp SprintBootService-1/target/*.jar .
                docker build -t ${IMAGE_NAME} .
                docker push ${IMAGE_NAME}
                kubectl apply -f deploy.yaml
                kubectl apply -f service.yaml
                """
            }
        }
    }
}
