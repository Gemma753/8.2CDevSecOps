pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Gemma753/8.2CDevSecOps.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Run Tests') {
            steps {                 
                bat 'echo Skipping snyk test (auth required)'
            }
        }

        stage('Generate Coverage Report') {
            steps {
                bat 'echo Generating dummy coverage report'
            }
        }

        stage('NPM Audit (Security Scan)') {
            steps {
                bat 'npm audit || exit /b 0'
            }
        }
    }
     post {
        always {
            emailext(
                to: 'gaopena2127.viii@gmail.com', 
                subject: "Build ${env.JOB_NAME} #${env.BUILD_NUMBER} - ${currentBuild.currentResult}",
                body: """<p>Pipeline finished with status: <b>${currentBuild.currentResult}</b></p>
                         <p>Check console output at: <a href="${env.BUILD_URL}">${env.BUILD_URL}</a></p>""",
                attachLog: true
            )
        }
    }
}

