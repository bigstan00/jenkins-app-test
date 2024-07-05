pipeline{
    agent any
    stages{
        stage("Test"){
            steps{
                echo "Welcome to your first class using Jenkins"
            }
        }
        stage("checkout something"){
            steps{
                echo "Welcome" >> index.txt
            }
        }
        stage("rolling") {
            steps{
                sh '''
                        echo "run" >> index.txt
                        cat index.txt
                        
                   '''
            }
        }
     }
}