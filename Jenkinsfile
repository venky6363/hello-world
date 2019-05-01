pipeline {
    agent 'master'
 tools{
  maven 'maven'
 }
    stages {
        stage('build') {
            steps {
                echo 'Clean Build'
                sh 'mvn clean compile'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing'
                sh 'mvn test'
            }
        }
        stage('Sonar') {
            steps {
                echo 'Sonar Scanner'
          withSonarQubeEnv('sonar') {
                sh 'mvn clean install  -D sonar.host.http://104.196.173.188:9000'
          }
          }
        }
        stage('Package') {
            steps {
                echo 'Packaging'
                sh 'mvn package'
            }
        
        }
    }
    
}
