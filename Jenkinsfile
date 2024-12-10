pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "MVN3"
    }

    stages {
        stage('pull-scm') {
            steps {
                // Get some code from a GitHub repository
                git credentialsId: 'github', url: 'git@github.com:damodar-reddy/jenkins_test.git'
            }
        }
        
        stage('build') {
            steps {
                sh "mvn -f api-gateway/ clean package"
            }
        }
        
        stage('publish') {
            steps {
                archiveArtifacts artifacts: 'api-gateway/target/*.jar', followSymlinks: false
                junit stdioRetention: '', testResults: 'api-gateway/target/surefire-reports/*.xml'
            }
        }

         stage('print') {
            steps {
                echo "testing"
            }
        }
    }
}
