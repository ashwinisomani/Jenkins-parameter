pipeline {
    agent any
        environment {
        GIT_REPO = "ssh://git@github.com:ashwinisomani/Jenkins-parameter.git"
        GIT_CREDENTIALS_ID = "asomani"
        GIT_BRANCH_NAME = "master"    
      
    }
  stages {
        stage('Get Code from Git') {
            steps {
                dir ('Jenkins-parameter') {
                    script {
                        scmVars =    checkout([
                                             $class: 'GitSCM', 
                                              branches: [[name: "${GIT_BRANCH_NAME}"]],
                                              doGenerateSubmoduleConfigurations: false, 
                                              extensions: [[$class: 'CleanCheckout']], 
                                              submoduleCfg: [], 
                                              userRemoteConfigs: [[credentialsId: "${GIT_CREDENTIALS_ID}", url: "${GIT_REPO}"]]
                                   ])
                    }
                  
                }
            }
        }
    }
}
