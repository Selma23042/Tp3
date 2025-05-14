pipeline {
    agent any

    environment {
        ANSIBLE_INVENTORY = 'inventaire.ini'
        ANSIBLE_PLAYBOOK = 'deploy.yml'
        SUDO_PASS = credentials('sudo-password')
    }

    stages {
        stage('Checkout') {
            steps {
                checkout([
                    $class: 'GitSCM',
                    branches: [[name: '*/master']],
                    userRemoteConfigs: [[
                        url: 'https://github.com/Selma23042/Tp3.git',
                        credentialsId: 'github-token-selma'
                    ]]
                ])
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
