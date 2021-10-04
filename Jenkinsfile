properties([parameters([choice(choices: ['RELEASE', 'SNAPSHOT'], description: 'buildType', name: 'buildType'), gitParameter(branch: '', branchFilter: '.*', defaultValue: '1.0.0', description: 'tag', name: 'tag', quickFilterEnabled: false, selectedValue: 'NONE', sortMode: 'NONE', tagFilter: '*', type: 'PT_TAG')])])



pipeline{
    agent none
    stages{
        stage('Checkout'){
            agent{
                label "master"
            }
            steps{
                echo "${params.tag}"
                echo "${params.buildType}"
                checkout([$class: 'GitSCM',   branches: [[name: refs/tags/"${params.tag}"]], extensions: [], userRemoteConfigs: [[credentialsId: 'Github_key', url: 'https://github.com/avinash11b11/TestRepo.git']]])
            }
        }
        
        stage('Snapshot Build'){
            agent{
                label "master"
            }
            when {
                    expression {params.buildType == 'SNAPSHOT'}
                }
            steps{
                
                bat'''
                call  mvn -f my-app/pom.xml versions:set -DnewVersion=%tag%-%buildType%
                call mvn -f my-app/pom.xml versions:commit
                call mvn -f my-app/pom.xml clean install 
               '''
            }
        }
        
        stage('Release Build'){
            agent{
                label "master"
            }
            when {
                    expression {params.buildType == 'RELEASE'}
                }
            steps{
                
                bat'''
                call  mvn -f my-app/pom.xml versions:set -DnewVersion=%tag%
                call mvn -f my-app/pom.xml versions:commit
                call mvn -f my-app/pom.xml clean install 
               '''
            }
        }
      
    }
}
