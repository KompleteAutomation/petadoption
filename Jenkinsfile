pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // Get some code from a GitHub repository
                git 'update-index --chmod=+x check_services.sh'
                git 'https://github.com/KompleteAutomation/petadoption.git'
				//sudo su
				//sh "chmod +x -R ${env.WORKSPACE}"
                // Run Maven Wrapper Commands
                sh "./mvnw compile"

                echo 'Building the Project with maven compile'
            }
        }

        stage('Test') {
            steps {

                // Run Maven Wrapper Commands
                sh "./mvnw test"

                echo 'Testing the Project with maven test'
            }
        }

        stage('Package') {
            steps {

                // Run Maven Wrapper Commands
                sh "./mvnw package"

                echo 'Packaging the Project with maven package'
            }
        }
        stage('Containerize') {
            steps {

                // Run Maven Wrapper Commands
                sh "docker build -t myapp ."

                echo 'Containerizing the App with Docker'
            }
        }
        stage('Deploy') {
            steps {

                // Run Maven Wrapper Commands
                sh "docker run -d -p 9090:9090 myapp"

                echo 'Deploy the App with Docker'
            }
        }
    }
}
