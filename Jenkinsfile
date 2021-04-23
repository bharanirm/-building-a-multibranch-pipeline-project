pipeline {
    agent any
   
    stages {
        stage('Build') {
            steps {
                sh 'echo "Hello world!"'
            }
        }
    }
     post {
    success {
          build job: 'multibranchpipeline',parameters: [string(name: 'Project_Name', value: 'test3'), 
                    string(name: 'Environment_Name', value: 'Dev_Env_1')]
            
                  }
      failure {
        echo "Not specified branch"
      /*  when {
      expression {
         return !env['GIT.BRANCH'].contains('feature/')
      }
    } */
        emailext (
         subject: "BUILD FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
         body: """BUILD FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':\n\nCheck console output at ${env.BUILD_URL}""",
         to: 'rmbharani@hotmail.com')
      }
     }
}
