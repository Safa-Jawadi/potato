pipeline {
    agent any
    tools {
      nodejs 'nodejs'
      dockerTool 'docker'
    }

    stages {
        stage('Npm Install') {
            steps {
                   sh 'npm install'
            }
        }

        stage('npm run build') {
            steps {
                   sh 'npm run build'
            }
        }
        stage('Docker Build') {
            steps {
                   sh '''
                       docker build -t documentation:1.0.1 . --target=production
                       docker build -t documentation:latest . --target=production
                   '''
            }
        }

        stage('Docker Push to Nexus') {
            steps {
                   sh '''
                    echo push image to nexus
                   '''
            }
        }



    }
}