pipeline {
    agent any 
    
    stages {
        stage('Distro Info') {
            steps {
                echo 'Informacoes da Distro utilizada:' 
                sh'cat /etc/*-release > /tmp/distro.info'
                               
            }
            
        }
        stage('Kernel Info') {
            steps {
                echo 'Informacoes do Kernel do Servidor:' 
                sh'uname -a > /tmp/kernel.info'
                
            }
        }
        stage('Users Info') {
            steps {
                echo 'Lista de Usuarios Presente no Servidor:' 
                sh'cat /etc/passwd | cut -d: -f1 > /tmp/users.info'
                                
            }
        }
        stage('Packages Info') {
            steps {
                echo 'Pacotes instalados no Servidor' 
                sh'dpkg -l > /tmp/packages.info'
                                
            }
        }
    }
    post {
        always { 
            echo 'Compilando o arquivo de assessment'
            sh "> assessment.txt"
            sh "cat /tmp/distro.info >> assessment"
            sh "cat /tmp/kernel.info >> assessment"
            sh "cat /tmp/users.info >> assessment"
            sh "cat /tmp/packages.info >> assessment"
        }
        success { 
            echo "Compilação efetuada com sucesso!"
        }
   
    }
    
}
