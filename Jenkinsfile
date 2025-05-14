pipeline {
    agent any

    environment {
        ANSIBLE_INVENTORY = 'inventaire.ini'
        ANSIBLE_PLAYBOOK = 'deploy.yml'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    credentialsId: 'github-token-selma', 
                    url: 'https://github.com/selma23042/Tp3.git'
            }
        }

        stage('Install Ansible') {
            steps {
                sh 'sudo apt update'
                sh 'sudo apt install -y ansible'
            }
        }

        stage('Run Ansible Playbook') {
            steps {
                ansiblePlaybook(
                    playbook: "${ANSIBLE_PLAYBOOK}",
                    inventory: "${ANSIBLE_INVENTORY}"
                )
            }
        }
    }
}
