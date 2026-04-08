@Library('Shared')_
pipeline{
    agent { label 'slave'}

    options {
            timestamps()
            disableConcurrentBuilds()
            buildDiscarder(logRotator(numToKeepStr: '10'))
            timeout(time: 30, unit: 'MINUTES')
        }


    stages{
        stage("Code clone"){
            steps{
            echo "Cloning the code"
            clone("https://github.com/swapnilgaikwad01-cloud/django-notes-app.git","main")
            echo "Cloning successful"
            }
        }

        stage("Code Build"){
                    steps{
                    dockerbuild("notes-app","latest")
                    }
                }
                stage("Push to DockerHub"){
                    steps{
                        dockerpush("dockerHubCreds","notes-app","latest")
                    }
                }
                stage("Deploy"){
                    steps{
                        deploy()
                    }
                }
    }

    post{
        success{
            echo "Pipline completed successfully"
        }
        failure{
           echo "Pipline failed"
        }
    }
}
