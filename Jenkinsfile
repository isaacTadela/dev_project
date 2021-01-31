pipeline {
agent any
stages {
    stage('Install requirements') {
        steps {
            bat 'pip install -r requirements.txt'
        }
    }
    stage('rest app') {
        steps {
            bat 'start /min python rest_app.py'
        }
    }
    stage('web app') {
        steps {
            bat 'start /min python web_app.py'
        }
    }
    stage('testing backend') {
        steps {
            bat 'python backend_testing.py'
        }
    }
    stage('testing frontend') {
        steps {
            bat 'python frontend_testing.py'
        }
    }
    stage('combined testing') {
        steps {
            bat 'python combined_testing.py'
        }
    }
    stage('clean environment') {
        steps {
            bat 'python clean_environment.py'
        }
    }
 }
 post {
        always {
            echo 'One way or another, I have finished'
            deleteDir() /* clean up our workspace */
        }
        success {
            echo 'I succeeded!'
        }
        failure {
            echo 'I failed :('

            mail to: 'iitzhakk@gmail.com',
                 subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
                 body: "Something is wrong with ${env.BUILD_URL}"
        }
    }
}