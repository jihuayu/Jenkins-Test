pipeline{
    agent any
    stages {
        stage('Build') {
            steps{
                echo 'Begin Build!'
                sh 'g++ -o main main.cpp' 
                archiveArtifacts artifacts: 'main', fingerprint: true
            }
        }
        stage('Test') {
            steps{
                echo 'Test Build!'
                sh './main'
            }
        }
        stage('Deploy') {
            when {
              expression {
                currentBuild.result == null || currentBuild.result == 'SUCCESS' 
              }
            }
            steps{
                echo 'This is a deploy step'    
            }
        }
    }
}