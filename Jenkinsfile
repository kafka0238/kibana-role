pipeline {
    agent {
        label 'linux'
    }
    stages {
        stage('Checkout') {
            steps {
                git credentialsId: '9804576d-4fc1-4ee2-8478-6138e22b6df2', url: 'git@github.com:kafka0238/kibana-role.git'
            }
        }
        stage('Install Molecule') {
            steps {
                sh 'pip3 install -r test-requirements.txt'
            }
        }
        stage('Add elastic role') {
            steps {
                sh 'git clone https://github.com/netology-code/mnt-homeworks-ansible.git molecule/default/roles/elastic'
            }
        }
        stage('Run Molecule') {
            steps {
                sh 'mkdir molecule/default/files'
                sh 'molecule test'
            }
        }
    }
}