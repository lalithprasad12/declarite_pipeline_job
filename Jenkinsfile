pipeline {
    agent any
    //agent { docker { image 'maven3.6.3'} }
    // agent 
     //{ docker { 
         //image 'maven'
      // } 
     //}
    
    
    
    
    
    
    
    stages {
        stage('Build') {
            steps {
                //sh label: '', script: 'mvn -v'
                echo "Build"
                echo "PATH - $PATH"
                echo "BUILD_NUMBER - $env.BUILD_NUMBER"
                echo "BUILD_ID - $env.BUILD_ID"
                echo "JOB_NAME - $env.JOB_NAME"
                echo "BUILD_TAG - $env.BUILD_TAG"
                echo "BUILD_URL - $env.BUILD_URL"
                }
            }
            
        stage('Test') {
            steps {
                echo "Test"
                }
            }
            
            
        stage('Integration Test') {
            steps {
                echo "Integration Test"
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

