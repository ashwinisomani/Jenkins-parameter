pipeline {
    agent any
       parameters {
        stringParam {
            name(BRANCH_NAME')
            defaultValue('master')
            description('Name of the branch in the git repo')
            trim(true)
        }
  }
                 
   stages {
        stage("Build") {
            steps {
                echo "stringParame: ${params.stringParam}"
            }
        }
    }
}               
