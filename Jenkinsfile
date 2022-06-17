pipeline {
    agent any
        environment {
        GIT_REPO = "git@github.com:ashwinisomani/Jenkins-parameter.git"
        GIT_CREDENTIALS_ID = "asomani"
          
      
    }
  stages {
        stage('Get Code from Git') {
            steps {
                dir ('Jenkins-parameter') {
                    script {
                        scmVars =    checkout([
                                             $class: 'GitSCM', 
                                              branches: [[name: "${branchName}"]],
                                              doGenerateSubmoduleConfigurations: false, 
                                              extensions: [[$class: 'CleanCheckout']], 
                                              submoduleCfg: [], 
                                              userRemoteConfigs: [[credentialsId: "${GIT_CREDENTIALS_ID}", url: "${GIT_REPO}"]]
                                   ])
                    }
                  
                }
            }
        }
      
      stage('Print Branch on Job') {
                       post {
                          failure {
                          slackSend (channel: 'xyz-build-failure', color: '#FF0000', message: """FAILED:
                         Job: ${GIT_CREDENTIALS_ID}
                         Build #${GIT_REPO})                    
                                },
                          success {
                         slackSend (channel: 'xyz-build-success', color: '#00FF00', message: """SUCCESS:
                          Job: ${env.GIT_CREDENTIALS_ID}
                          Build #${env.GIT_REPO})
                               }
                          }
          }
    }
}
