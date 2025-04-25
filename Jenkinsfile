pipeline {
    agent any

    stages {
        stage("Repo Code Checkout") {
            steps {
                script {
                    echo "1st Step to checkout the github repository.... "
                    git branch: 'main', credentialsId: 'github-id', url: 'https://github.com/waseemuddin/test-pipeline.git'
            }
        }
    }
        stage("Image Build") {
            steps {
                script {
                     echo "2nd Step to building the image......"
                    }
                }
            }
        stage("Image Push") {
            steps {
                script {
                    echo "3rd Step is to pushing the image to docker hub repo...."

                }
            }
        }
        stage("Create Container") {
            steps {
                script {
                    echo "4th step is to create the docker container and run...."
                }
            }
        }

    }
}




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
//                 withCredentials([usernamePassword(credentialsId: 'docker-hub-id', passwordVariable: 'PASS', usernameVariable: 'USER')]) {
                    
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