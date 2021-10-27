pipeline {
    agent any 
    
    stages {
        stage('Distro Info') {
            steps {
                sh'echo "Informacoes da Distro utilizada $(hostname -i):" >> assessment.txt'
                cat /etc/*-release >> assessment.txt
                sh'echo "================================" >> assessment.txt'
                sh'echo "================================" >> assessment.txt'                
            }
            
        }
        stage('Kernel Info') {
            steps {
                sh'echo "Informacoes do Kernel do Servidor $(hostname -i):" >> assessment.txt'
                uname -a >> assessment.txt
                sh'echo "================================" >> assessment.txt'
                sh'echo "================================" >> assessment.txt'
            }
        }
        stage('Users Info') {
            steps {
                sh'echo "Lista de Usuarios Presente no Servidor $(hostname -i):" >> assessment.txt'
                cat /etc/passwd | cut -d: -f1 >> assessment.txt 
                sh'echo "================================" >> assessment.txt'
                sh'echo "================================" >> assessment.txt'
                
            }
        }
        stage('Packages Info') {
            steps {
                sh'echo "Pacotes instalados no Servidor $(hostname -i):" >> assessment.txt'
                dpkg -l >> assessment.txt'
                sh'echo "================================" >> assessment.txt'
                sh'echo "================================" >> assessment.txt'
                
            }
        }
    }
    post {
        always { echo "Eu sempre vou ser executado!"}
        success { echo "Somente serei executado quando finalizar com sucesso!"}
        failure { echo "Somentei serei executado quando finalizar com erro!"}
    }
    
}
