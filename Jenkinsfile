pipeline {
    agent any
    tools {
      nodejs 'nodejs'
      dockerTool 'docker'
    }

    stages {

        stage('Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/safa-jawadi/potato'
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