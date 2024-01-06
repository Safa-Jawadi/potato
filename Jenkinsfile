pipeline {
    agent any
    options {
        ansiColor('xterm')
    }
    tools {
      nodejs 'nodejs'
      dockerTool 'docker'
    }
    environment {
        NEXUS_URL = "localhost:8085"  // Replace with your Nexus URL
        NEXUS_REPO = "documentation"        // Replace with your Nexus repository name
        DOCKER_IMAGE_NAME = "doc"  // Replace with your Docker image name
        DOCKER_IMAGE_TAG = "1.2.0"    // Replace with your Docker image tag
    }

    stages {

        stage('Clone') {
            steps {
                git branch: 'main', url: 'git@github.com:Safa-Jawadi/potato.git'
            }
        }

       stage('SonarQube Analysis') {
                environment {
                    SONAR_PROJECT_KEY = 'doc'
                    SONAR_SOURCES_DIR = './src'
                    SONAR_HOST_URL = 'http://sonarqube:9000'
                }
                agent {
                    docker {
                        image 'sonarsource/sonar-scanner-cli'
                        args "-v /var/run/docker.sock:/var/run/docker.sock --network devops"
                    }
                }
                steps {
                    withCredentials([string(credentialsId: 'sonarqubetoken', variable: 'SONAR_TOKEN')]) {
                        script {
                            sh """
                            sonar-scanner \\
                                -Dsonar.projectKey=${SONAR_PROJECT_KEY} \\
                                -Dsonar.sources=${SONAR_SOURCES_DIR} \\
                                -Dsonar.host.url=${SONAR_HOST_URL} \\
                                -Dsonar.token=${SONAR_TOKEN} \\
                              
                            """
                        }
                    }
                }
            }

        stage('Docker Build') {
            steps {    
             sh 'docker build -t "${NEXUS_URL}/${DOCKER_IMAGE_NAME}:${DOCKER_IMAGE_TAG}" --target=production .'
            }   
        }

        stage('Docker Push to Nexus') {
            steps {
                script {
                
                    // Login to Nexus Docker registry
                    withCredentials([usernamePassword(credentialsId: 'nexusCredentials', passwordVariable: 'NEXUS_PASSWORD', usernameVariable: 'NEXUS_USERNAME')]) {
                         sh "docker login  ${NEXUS_URL} -u ${NEXUS_USERNAME} -p ${NEXUS_PASSWORD}"

                    }

                    // Push the Docker image to Nexus
                    sh "docker push ${NEXUS_URL}/${DOCKER_IMAGE_NAME}:${DOCKER_IMAGE_TAG}"
                }
            }
        }



    }
}