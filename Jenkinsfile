properties([parameters([gitParameter(branch: '', branchFilter: '.*', defaultValue: '1.0.0', description: 'tag', name: 'tag', quickFilterEnabled: false, selectedValue: 'NONE', sortMode: 'NONE', tagFilter: '*', type: 'PT_TAG')])])

pipeline{
    agent none
    stages{
        stage('Non-Parallel Stage'){
            agent{
                label "master"
            }
            steps{
                checkout([$class: 'GitSCM',   branches: [[name: "${params.TAG}"]], extensions: [], userRemoteConfigs: [[credentialsId: 'Github_key', url: 'https://github.com/avinash11b11/TestRepo.git']]])
            }
        }
      
    }
}
