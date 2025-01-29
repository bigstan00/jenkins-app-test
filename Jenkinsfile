pipeline {
    agent any
    stages {
        stage("Test") {
            steps {
                echo "Welcome to Your first Multibranch Jenkins-class"
            }
        }
        stage("checkout something") {
            steps {
                sh '''
                    echo "Welcome" > index.txt
                '''
            }
        }
        stage("rolling") {
            steps {
                sh '''
                    echo $HOME
                    pwd
                    echo "Hello World" taller.txt
                '''
            }
        }
        stage("install nginx"){
            steps {
                sh '''
                     set -e  # Exit on failure
            
                    # Update package lists and upgrade
                    sudo apt-get update
                    sudo apt-get upgrade -y
            
                    # Install NGINX if not already installed
                    sudo apt-get install nginx -y
                    sudo systemctl enable nginx
            
                    # Ensure NGINX is running
                    sudo systemctl restart nginx
                    '''
            }
        }
        stage("build"){
            steps{
                sh '''
                    sudo chown -R jenkins:jenkins /var*
                    cd /var/www
                    sudo rm -rf html
                    sudo mkdir html
                    cd html
                

                '''
            }
        }
        stage("deploy"){
            steps{
                sh '''
                    sudo git clone https://github.com/bigstan00/pix-mix.git
                '''
            }
        }
    }
}