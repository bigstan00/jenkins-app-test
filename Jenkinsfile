pipeline {
    agent any
    options {
        buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '30', numToKeepStr: '5')
        }
        stage("Install Nginx") {
            steps {
                sh '''
                    set -e  # Exit on failure

                    # Update package lists and upgrade
                    sudo apt-get update -y
                    sudo apt-get upgrade -y

                    # Install NGINX if not already installed
                    if ! dpkg -l | grep -q nginx; then
                        sudo apt-get install nginx -y
                    fi

                    # Test Nginx configuration
                    sudo nginx -t || { echo "Nginx configuration test failed"; exit 1; }

                    # Enable and restart NGINX
                    sudo systemctl enable nginx
                    sudo systemctl restart nginx || { echo "Nginx failed to start"; sudo systemctl status nginx.service; exit 1; }
                '''
            }
        }
        stage("Build") {
            steps {
                sh '''
                    # Create /var/www/html if it doesn't exist
                    sudo mkdir -p /var/www/html

                    # Ensure Jenkins has access to /var/www/html
                    sudo chown -R jenkins:jenkins /var/www/html
                    cd /var/www/html
                    sudo rm -rf ./*
                '''
            }
        }
        stage("Deploy") {
            steps {
                sh '''
                    # Clone the repository
                    if ! sudo -u jenkins git clone https://github.com/bigstan00/pix-mix.git /var/www/html; then
                        echo "Failed to clone the repository. Check the URL or permissions."
                        exit 1
                    fi
                '''
            }
        }
    }
    post {
        success {
            echo "Pipeline succeeded!"
        }
        failure {
            echo "Pipeline failed. Check the logs for details."
        }
    }
}