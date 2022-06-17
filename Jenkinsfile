pipeline {
    agent any
        environment {
        GIT_REPO = "git@github.com:ashwinisomani/Jenkins-parameter.git"
        GIT_CREDENTIALS_ID = "asomani"
        GIT_BRANCH_NAME = "*/main"    
          
      
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
      
      stage('Print Branch on Job') {
           environment {
           CURRENT_BRANCH_NAME = "${GIT_BRANCH_NAME.split('/').size() > 1 ? GIT_BRANCH_NAME.split('/')[1..-1].join('/') : GIT_BRANCH_NAME}"
            }
          steps {
               script{
                   currentBuild.displayName = "#"+currentBuild.rawBuild+": "+CURRENT_BRANCH_NAME
                }
             }
          }
       }
   }
