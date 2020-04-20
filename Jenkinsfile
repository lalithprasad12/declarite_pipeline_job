pipeline {
    agent any
    //agent { docker { image 'maven3.6.3'} }
    // agent 
     //{ docker { 
         //image 'maven'
      // } 
     //}
    
    environment {
        mavenHome = tool 'MVN_HOME'
        dockerHome = tool 'DOCKER_HOME'
        PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"        
    }  
    
    stages {
        stage('CHeckout') {
            steps {
                sh label: '', script: 'mvn -v'       
                sh label: '', script: 'docker --version'
                echo "Build"
                echo "PATH - $PATH"
                echo "BUILD_NUMBER - $env.BUILD_NUMBER"
                echo "BUILD_ID - $env.BUILD_ID"
                echo "JOB_NAME - $env.JOB_NAME"
                echo "BUILD_TAG - $env.BUILD_TAG"
                echo "BUILD_URL - $env.BUILD_URL"
                }
            }
        
         stage('Compile') {
            steps {
                sh label: '', script: 'mvn clean compile'
                }
            }
            
        stage('Test') {
            steps {
                sh label: '', script: 'mvn test'
                }
            }
            
            
        stage('Integration Test') {
            steps {
                sh label: '', script: 'mvn failsafe:integration-test failsafe:verify'
                }
            }    
        
        
         stage('Package') {
            steps {
                sh label: '', script: 'mvn package -DskipTests'
                }
            }         
        
        
        
        
         stage('Build Docker Image') {
            steps {
                //sh docker build -t n28min/currency-exchange-devops:$env.BUILD_TAG
                script {
                    dockerImage = docker.build ("lalithprasad12/hello-world-python:${env.BUILD_TAG}")
                    }
                }
            }
        
         stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('', 'dockerhub') {
                        dockerImage.push();
                        dockerImage.push('latest);
                        }
                    }
                }
            }
        
        
        
        
            
        }
        
        
            post {
                always {
                    echo "I am awseome, I run alaways"
                    }
                success {
                    echo "I run when its a success"
                    }
                failure {
                    echo "I run whan its a failure"
                    }
                }
        
           }

