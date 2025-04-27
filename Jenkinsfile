pipeline {
    agent any

    stages {
        stage ("code checkout") {
            steps {
                script {
                    try {
                        echo "This is Git Checkout Stage....."   
                        git branch: 'main', credentialsId: 'github-id', url: 'https://github.com/waseemuddin/test-pipeline.git'
                    } catch (err) {
                        echo "Checkout failed: ${err}"
                        error("Stopping Pipeline due to checkout failure!")
                    }
                }
            }
        }

        stage("image build") {
            steps {
                script {
                    try {
                        echo "This is Image Building....."
                        sh 'docker image build -t waseem63/mydockerapp:v$BUILD_ID .'
                        sh 'docker image tag waseem63/mydockerapp:v$BUILD_ID waseem63/mydockerapp:latest'
                    } catch (err) {
                        echo "Image build failed: ${err}"
                        error("Stopping Pipeline due to build failure!")
                    }
                }
            }
        }

        stage("image push") {
            steps {
                script {
                    try {
                        echo "This is Image Pushing Stage......"
                        withCredentials([usernamePassword(credentialsId: 'docker-hub-idw', passwordVariable: 'PASS', usernameVariable: 'USER')]){
                            sh "echo $PASS | docker login -u $USER --password-stdin"
                            sh 'docker push waseem63/mydockerapp:v$BUILD_ID'
                            sh 'docker push waseem63/mydockerapp:latest'
                            sh 'docker rmi waseem63/mydockerapp:v$BUILD_ID waseem63/mydockerapp:latest'
                        }
                    } catch (err) {
                        echo "Image push failed: ${err}"
                        error("Stopping Pipeline due to push failure!")
                    }
                }
            }
        }

        stage("container creating") {
            steps {
                script {
                    try {
                        echo "This is Container Creating Stage......"
                        sh 'docker run -itd --name todoapp -p 3000:3000 waseem63/mydockerapp:latest'
                    } catch (err) {
                        echo "Container creation failed: ${err}"
                        error("Stopping Pipeline due to container creation failure!")
                    }
                }
            }
        }
    }
}




// pipeline {
//     agent any

//     stages {
//         stage ("code checkout"){
//             steps {
//                 script {
                 
//                   echo "This is Git Checkout Stage....."   
//                   git branch: 'main', credentialsId: 'github-id', url: 'https://github.com/waseemuddin/test-pipeline.git'
            
//                 }
//             }

//         }

//         stage("image build") {
//              steps {
//                 script {
//                  echo "This is Image Building....."
//                  sh 'docker image build -t waseem63/mydockerapp:v$BUILD_ID .'
//                  sh 'docker image tag waseem63/mydockerapp:v$BUILD_ID waseem63/mydockerapp:latest'

//                 }
//              }
//          }
//         stage("image push") {
//             steps {
//                 script {
//                         echo "This is Image Pushing Stage......"
//                         withCredentials([usernamePassword(credentialsId: 'docker-hub-idw', passwordVariable: 'PASS', usernameVariable: 'USER')]){
//                         sh "echo $PASS | docker login -u $USER --password-stdin"
//                         sh 'docker push waseem63/mydockerapp:v$BUILD_ID'
//                         sh 'docker push waseem63/mydockerapp:latest'
//                         sh 'docker rmi waseem63/mydockerapp:v$BUILD_ID waseem63/mydockerapp:latest'
//                    }
//                 }
//             }
//         }
//             stage("container creating") {
//                 steps {
//                   script {
//                     echo "This is Container Creating Stage......"
//                     sh 'docker run -itd --name todoapp -p 3000:3000 waseem63/mydockerapp:latest'
                 
//                   }
                  

//                 }
//             }
        
//     }
// }






// pipeline {
//     agent any

//     stages {
//         stage("Code checkout") {
//             steps {
//                git branch: 'main', credentialsId: 'github-id', url: 'https://github.com/waseemuddin/simple-cicd-project01.git'
//             }
//         }
//         stage("image build") {
//             steps {
//                 echo "image building....."
//                 sh 'docker image build -t waseem63/mydockerapp:v$BUILD_ID .'
//                 sh 'docker image tag waseem63/mydockerapp:v$BUILD_ID waseem63/mydockerapp:latest'
//             }
//         }
//         stage("Image Push") {
//             steps {
//                 withCredentials([usernamePassword(credentialsId: 'docker-hub-id-w', passwordVariable: 'PASS', usernameVariable: 'USER')]) {
                    
//                     sh "echo $PASS | docker login -u $USER --password-stdin"
//                     sh 'docker push waseem63/mydockerapp:v$BUILD_ID'
//                     sh 'docker push waseem63/mydockerapp:latest'
//                     sh 'docker rmi waseem63/mydockerapp:v$BUILD_ID  waseem63/mydockerapp:latest'
//                 }
//             }
            
//         }
//         stage("Container Creating") {
//             steps {
//                 sh 'docker run -itd --name todoapp -p 3000:3000 waseem63/mydockerapp:latest'
            
//             }
//         }
        
//     }
// }