pipeline {
    agent any 
    
    stages {
        stage('Distro Info') {
            steps {
                echo "Informacoes da Distro utilizada $(hostname -i):" 
                sh'cat /etc/*-release >> assessment.txt'
                               
            }
            
        }
        stage('Kernel Info') {
            steps {
                echo "Informacoes do Kernel do Servidor $(hostname -i):" 
                sh'uname -a >> assessment.txt'
                
            }
        }
        stage('Users Info') {
            steps {
                echo "Lista de Usuarios Presente no Servidor $(hostname -i):" 
                sh'cat /etc/passwd | cut -d: -f1 >> assessment.txt'
                                
            }
        }
        stage('Packages Info') {
            steps {
                echo "Pacotes instalados no Servidor $(hostname -i):" 
                sh'dpkg -l >> assessment.txt'
                                
            }
        }
    }
    post {
        always { 
            echo 'Compilando o arquivo de assessment'
            sh "> assessment.txt"
            sh "cat /tmp/ditro.info >> assessment"
            sh "cat /tmp/kernel.info >> assessment"
            sh "cat /tmp/users.info >> assessment"
            sh "cat /tmp/packages.info >> assessment"
        }
        success { echo "Compilação efetuada com sucesso!"}
        
    }
    
}
