pipeline {
    agent any
    stages {
        stage('git clone') {
            steps {
              git branch: 'main',url: "https://github.com/Venkatnagaraj38/Apache_ansible.git" 
              sh "ls -ll"
            }
        }
        stage('playbook') {
            steps {
                //ansiblePlaybook credentialsId: 'webserverpasswd', disableHostKeyChecking: true, inventory: 'inventory', playbook: 'installing_apache2.yml'
                ansiblePlaybook credentialsId: 'qapassword', disableHostKeyChecking: true, inventory: 'inventory', playbook: 'qa.yml'
            }
        }
    }
    post {
            success {
                mail (to: 'venkatnagaraj038@gmail.com',
         subject: "Job '${env.JOB_NAME}'- (${env.BUILD_NUMBER}) has SUCCEED",
         body: "Please go to ${env.BUILD_URL} for more details. ");
            }
            failure {
                mail (to: 'venkatnagaraj038@gmail.com',
         subject: "Job '${env.JOB_NAME}'- (${env.BUILD_NUMBER}) has FAILED",
         body: "Please go to ${env.BUILD_URL} for more details. ");
            }
        }
}
