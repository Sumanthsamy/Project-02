pipeline {
    agent any
    environment {
        PATH = "/usr/local/src/apache-maven/bin:$PATH"
    }
    stages {
        stage('GitHub Clone') {
            steps {
                git branch: 'Project-02', url: 'https://github.com/Sumanthsamy/Project-02.git'
            }
        }
        stage('Build Maven') {
            steps {
                sh "mvn clean package"
            }
        }
        stage('Deploy Tomcat') {
            steps {
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'Tomcat-credentials',
                path: '', 
                url: 'http://13.203.203.38:8080/')], 
                contextPath: 'Project-02', 
                war: '**/*.war'
            }
        }
    }
    
}