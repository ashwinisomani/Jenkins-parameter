pipeline {
    agent any
        environment {
        GIT_REPO = "git@github.com:ashwinisomani/Jenkins-parameter.git"
        GIT_CREDENTIALS_ID = "ashwini.somanisap5@gmail.com"
        GIT_BRANCH_NAME = "Jenkins-parameter"
    }
  stages {
        stage('Get Code from Git') {
            steps {
                dir ('Jenkins-parameter') {
                    script {
                        scmVars =   checkout([
                                        $class: 'GitSCM',
                                        branches: [[name: "${GIT_BRANCH_NAME}"]],
                                        doGenerateSubmoduleConfigurations: false,
                                        extensions: [
                                        [$class: 'SubmoduleOption',
                                        disableSubmodules: false,
                                        parentCredentials: true,
                                        recursiveSubmodules: true,
                                        reference: '',
                                        trackingSubmodules: false],
                                        [$class: 'CleanBeforeCheckout']],
                                        submoduleCfg: [],
                                        userRemoteConfigs: [[credentialsId: "${GIT_CREDENTIALS_ID}", url: "${GIT_REPO}"]]
                                    ])
                    }
                }
            }
        }
    }
}
