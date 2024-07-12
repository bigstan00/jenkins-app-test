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
                    sudo apt-get update
                    sudo apt upgrade -y
                    sudo apt-get install nginx -y
                    sudo systemctl enable nginx
                    sudo systemctl start nginx
                '''
            }
        }
        stage("build"){
            steps{
                sh '''
                    sudo chown -R jenkins:jenkins /var*
                    cd /var
                    sudo rm -rf www
                    sudo mkdir www
                    cd /var/www

                '''
            }
        }
        stage("deploy"){
            steps{
                sh '''
                    cd /var/www/html
                    sudo git clone https://github.com/bigstan00/pix-mix.git /html
                '''
            }
        }
    }
}
