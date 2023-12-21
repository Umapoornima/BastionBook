    agent any

    environment {
        // Define environment variables if needed
        PYTHON_VERSION = '3.8'
    }

    stages {
        stage('Checkout') {
            steps {
                // Check out the code from the Git repository
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                // Install Python dependencies using a virtual environment
                sh "python${PYTHON_VERSION} -m venv venv"
                sh "venv/bin/pip install -r requirements.txt"
            }
        }

        stage('Run Tests') {
            steps {
                // Run tests (adjust the testing command as per your project)
                sh "venv/bin/python -m unittest discover -s tests -p '*_test.py'"
            }
        }

        stage('Build') {
            steps {
                // Build your application (e.g., create distribution packages)
                sh "python${PYTHON_VERSION} setup.py sdist bdist_wheel"
            }
        }

        stage('Deploy') {
            steps {
                // Your deployment steps (e.g., deploy to a server)
                // Adjust the deployment command based on your deployment strategy
                sh 'deploy-script.sh'
            }
        }
    }

    post {
        always {
            // Clean up or perform additional actions after the pipeline runs
            // For example, clean up temporary files, notify stakeholders, etc.
        }

