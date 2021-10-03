pipeline{
    agent none
    stages{
        stage('Non-Parallel Stage'){
            agent{
                label "master"
            }
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/${params.tag}']], extensions: [], userRemoteConfigs: [[credentialsId: 'Github_key', url: 'https://github.com/avinash11b11/TestRepo.git']]])
            }
        }
      
    }
}
