pipeline{
  
   agent {
      label 'master'
  }

  stages{

    stage('Verify'){
        steps{
            sh "ssh damy2@192.168.152.131 'ls -al'"
        }
    }
  }
}
