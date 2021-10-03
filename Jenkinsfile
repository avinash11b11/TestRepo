pipeline{
    agent none
    stages{
        stage('Non-Parallel Stage'){
            agent{
                label "master"
            }
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'Github_key', url: 'https://github.com/avinash11b11/TestRepo.git']]])
            }
        }
        
        stage('Run Tests'){
            parallel{
                stage('Test on windows'){
                    agent{
                        label "Windows_Node1"
                    }
                    steps{
                        echo "Task1 on agent"
                    }
                }
                stage('Test on Master'){
                    agent{
                        label "master"
                    }
                    steps{
                        echo "Task1 on master"
                    }
                }
            }
        }
    }
}
