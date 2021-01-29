pipeline {
agent any
stages {
    stage('pull from git') {
        steps {
            bat 'git clone https://github.com/isaacTadela/dev_project'
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
            bat 'py backend_testing.py'
        }
    }
    stage('testing frontend') {
        steps {
            bat 'py frontend_testing.py'
        }
    }
    stage('combined testing') {
        steps {
            bat 'py combined_testing.py'
        }
    }
    stage('clean environemnt') {
        steps {
            bat 'py clean_environment.py'
        }
    }
 }
 post {
        always {
            echo 'One way or another, I have finished'
            cleanWs()
        }
        success {
            echo 'I succeeded!'
        }
        unstable {
            echo 'I am unstable :/'
        }
        failure {
            echo 'I failed :('
        }
        changed {
            echo 'Things were different before...'
        }
    }
}