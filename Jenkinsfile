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
        TEST_NAME = "Pipeline-env"
    }
    stages{
        stage('Clone'){
            steps{
                git "$GIT_REPO"
               // sh 'exit 1'
            }
            post{
                success{
                    sh 'echo "Clone Successful"'
                }
                always{
                    sh 'echo "Welcome To Pipeline"'
                }
                failure{
                    sh 'echo "Cloning Failed. Sending Notification"'
                }
            }
        }
        stage("Build"){
            steps{
                sh 'mvn clean install'
            }
        }
        stage("Testing Stage"){
            environment{
                TEST_NAME = "stage-env"
            }
            parallel{
                stage("Testing"){
                    steps{
                        sh 'echo "$TEST_NAME"'
                    }
                }
                stage("Test on Windows"){
                    // agent {label "windows-machine"}
                    steps{
                        sh 'echo "Substage 1"'
                    }
                }
                stage("Test on Linux"){
                    // agent {label "linux-machine"}
                    steps{
                        sh 'echo "Substage 2"'
                    }
                }
            }
        }
    }
    post{
        always{
            sh 'echo "Running for Pipeline"'
        }
    }
}