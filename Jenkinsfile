pipeline {

    agent {
        node {
            label 'master'
        }
    }

    tools { 
        maven 'maven3' 
    }

    options {
        buildDiscarder logRotator( 
                    daysToKeepStr: '15', 
                    numToKeepStr: '10'
            )
    }

    environment {
        APP_NAME = "STUDENT_APP"
        APP_ENV  = "DEV"
    }

    stages {
        
        stage('S1_22050069') {
            steps {
                cleanWs()
                sh """
                echo "S1_22050069: Environment Preperation Completed"
                """
            }
        }

        stage('S2_22050069') {
            steps {
                sh 'docker rm 22050069_svr '
                sh 'docker run -d -it -p 42000:80 --name=22050069_svr 22050112_webimage bash -c "service apache start && sleep 60"'
                sh 'docker start 22050069_svr'
                sh """
                echo "S2_22050069: Web Server Creation Completed"
                sh """
            }
        }
        
        stage('S_Parallel_22050069') {
            
            parallel {
                stage('S3_22050069') {        
            steps {
                sh """
                echo "S3_22050069: API Test Completed"
                """
            }
        }
        stage('S4_22050069') {
            steps {
                 sh 'echo "S4_22050069: DAST Security Completed"'
            }
        }
   }
        stage('S5_22050069') {
            input {
                message "Do you want to release the work?"
                ok "yes"
            }
            
            steps {
                echo "S5_Print out"            }
        }

    }   
        stage('S6_22050069') {
            steps {
                sh 'echo "Work release - 22050069"'
            }    
        }
}
    
}
