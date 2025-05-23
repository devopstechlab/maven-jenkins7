pipeline {
    agent any
    tools {
        jdk 'java17'
        maven 'maven3'
    }
    stages{
        stage('git code dewnload'){
            steps{
                echo 'Download code from Git'
                git branch: 'main', url: 'https://github.com/Shrujal82/maven-jenkins7.git'
            }
        }
        stage('Build'){
            steps{
                echo 'Build java project'
                sh 'mvn clean package'
            }
        }
        stage('Archive artifact'){
            steps{
                echo 'Archive artifacts'
                archiveArtifacts artifacts: '**/*.war', followSymlinks: false
            }
        }
         stage('Build Other Job'){
            steps{
                echo 'Build Other Job'
                build wait: false, job: 'deploy-pipeline'
            }
        }
    }
}
