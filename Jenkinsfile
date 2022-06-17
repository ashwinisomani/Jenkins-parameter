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
          steps {
               script{
                  
                   def commit = scmVars.GIT_COMMIT
                   def branch = scmVars.GIT_BRANCH
                   currentBuild.description = "+branch+"/"+commit
            
                }
             }
          }
       }
   }
