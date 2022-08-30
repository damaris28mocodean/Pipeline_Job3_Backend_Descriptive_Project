pipeline{
  
   agent {
      label 'master'
  }

  stages{

    stage ('Setup parameters'){
       
        steps{
          
          script{
            properties([
                      parameters([
                        string(defaultValue: 'damy28/backend_repo', name: 'IMAGE_NAME', description: ''),
                        string(defaultValue: 'backend_cont', name: 'CONTAINER_NAME', description: ''),
                        string(defaultValue: 'damy2', name: 'REMOTE_SERVER_USER', description: ''),
                        string(defaultValue: '192.168.152.131', name: 'REMOTE_SERVER_IP', description: '')
                      ])
            ])
          }
        }
    }

    stage('Stop and delete container'){
        steps{
            sh "${REMOTE_SERVER_USER}@${REMOTE_SERVER_IP} 'docker stop ${CONTAINER_NAME}'"
            sh "${REMOTE_SERVER_USER}@${REMOTE_SERVER_IP} 'docker rm ${CONTAINER_NAME}'"
        }
    }
    stage('Delete all the images'){
        steps{
            sh "ssh damy2@192.168.152.131 'docker run --name ${CONTAINER_NAME} -d -p ${PORT}:8080 ${IMAGE_NAME}:20'"
        }
    }
  }
}
