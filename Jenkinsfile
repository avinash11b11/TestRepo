properties([parameters([choice(choices: ['RELEASE', 'SNAPSHOT'], description: 'buildType', name: 'buildType'), gitParameter(branch: '', branchFilter: '.*', defaultValue: '1.0.0', description: 'tag', name: 'tag', quickFilterEnabled: false, selectedValue: 'NONE', sortMode: 'NONE', tagFilter: '*', type: 'PT_TAG')])])

pipeline{
    agent none
    stages{
        stage('Non-Parallel Stage'){
            agent{
                label "master"
            }
            steps{
                echo "${params.tag}"
                echo "${params.buildType}"
                checkout([$class: 'GitSCM',   branches: [[name: "1.0.4"]], extensions: [], userRemoteConfigs: [[credentialsId: 'Github_key', url: 'https://github.com/avinash11b11/TestRepo.git']]])
            }
        }
      
    }
}
