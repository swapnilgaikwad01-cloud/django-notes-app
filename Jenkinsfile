@Library('Shared')_
pipeline{
    agent { label 'slave'}
    
    stages{
        stage("Code clone"){
            steps{
            echo "Cloning the code"
            clone("https://github.com/swapnilgaikwad01-cloud/django-notes-app.git","main")
            echo "Cloning successful"
            }
        }
    }
}
