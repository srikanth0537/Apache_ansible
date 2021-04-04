pipeline {
    agent any
    stages {
        stage('git clone') {
            steps {
              git branch: 'main',url: "https://github.com/sajjavenkey50/Apache_ansible.git" 
              sh "ls -ll"
            }
        }
        stage('playbook') {
            steps {
                ansiblePlaybook credentialsId: 'ansible_login', disableHostKeyChecking: true, inventory: 'inventory', playbook: 'remove_apache2.yml'
            }
        }
    }
    post {
            success {
                mail to:"example@gmail.com, example05@gmail.com", subject:"SUCCESS: ${currentBuild.fullDisplayName}", body: "Yay, we passed."
            }
            failure {
                mail to:"example@gmail.com, example@gmail.com", subject:"FAILURE: ${currentBuild.fullDisplayName}", body: "Boo, we failed."
            }
        }
}
