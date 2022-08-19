pipeline {
    agent any

    stages {
        
        stage('Clone') {
            steps {
                // Get some code from a GitHub repository
                git 'https://github.com/gopiteekenam/docker-java-sample.git'
            }
            
        }
        
        stage('Build') {
            steps {

                // Run Maven on a Unix agent.
                // sh "mvn -Dmaven.test.failure.ignore=true clean package"

                // To run Maven on a Windows agent, use
                bat "mvn clean install -DskipTests"
            }
        }
        
        stage('docker package') {
            steps {
                bat 'docker build -t dockerjava .'
            }
        }
        
//         stage('docker login') {
//             steps {
//                 	bat 'docker login -u gopiteekenam -p 48cc7b0c-36c1-4ee8-b762-053f950813b0'
//             }
//         }
        
//         stage('docker push') {
//             steps {
//                 bat 'docker push dockerjava:latest'
//             }
//         }
        
        stage('docker deploy') {
            steps {
                bat 'docker run -d -p 9090:8080 gopiteekenam/springboot-dockerfile'
            }
        }
                
    }
}
