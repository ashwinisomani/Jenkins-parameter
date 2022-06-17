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
           environment {
           CURRENT_BRANCH_NAME = "${GIT_REPO.split('/').size() > 1 ? GIT_REPO.split('/')[1..-1].join('/') : GIT_REPO}"
            }
          steps {
               script{
                   currentBuild.displayName = "#"+currentBuild.number+": "+CURRENT_BRANCH_NAME
                }
             }
          }
       }
   }
