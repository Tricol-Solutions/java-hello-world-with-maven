// pipeline{
//     agent any

//     tools {
//          maven 'maven'
//          jdk 'java'
//     }

//     stages{
//         stage('checkout'){
//             steps{
//                 checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'github access', url: 'https://github.com/sreenivas449/java-hello-world-with-maven.git']]])
//             }
//         }
//         stage('build'){
//             steps{
//                bat 'mvn package'
//             }
//         }
//     }
// }

// node{
//     stage(){

//     },
//     stage(){

//     }
// }

pipeline{
    agent any
    environment {
        GIT_REPO = "https://github.com/Tricol-Solutions/java-hello-world-with-maven.git"
    }
    stages{
        stage('Clone'){
            steps{
                git "$GIT_REPO"
            }
            post{
                sh 'echo "Clone Successful"'
            }
        }
        stage("Build"){
            steps{
                sh 'mvn clean install'
            }
        }
    }
}