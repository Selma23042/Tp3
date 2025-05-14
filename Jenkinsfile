pipeline {
    agent any

    environment {
        ANSIBLE_INVENTORY = 'inventaire.ini'
        ANSIBLE_PLAYBOOK = 'deploy.yml'
        SUDO_PASS = credentials('s49196554')
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master',
                    credentialsId: 'github-token-selma',
                    url: 'https://github.com/selma23042/Tp3.git'
            }
        }

        stage('Install Ansible') {
            steps {
                sh 'echo "$SUDO_PASS" | sudo -S apt update'
                sh 'echo "$SUDO_PASS" | sudo -S apt install -y ansible'
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
