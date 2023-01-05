pipeline {
    agent any

    stages {
        stage('Building') {
            steps {
                // Pull the code from Github
                bat 'pip install -r requirements.txt'
            }
        }
        stage('Testing') {
            steps {
                // Install the python flask application and run the tests
                
                bat 'python -m unittest'
            }
        }
        stage('Deploying') {
            steps {
                // Build the Docker image
                bat 'docker build -t github-jenkins-leolb .'
                // Run a docker container from the image
                bat 'docker run -d -p 5000:5000 github-jenkins-leolb'
            }
        }
    }

    // Listen for Github webhooks
    triggers {
        githubPush()
    }
}
