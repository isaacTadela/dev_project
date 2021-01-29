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
            bat 'start /min python backend_testing.py'
        }
    }
    stage('testing frontend') {
        steps {
            bat 'start /min python frontend_testing.py'
        }
    }
    stage('combined testing') {
        steps {
            bat 'start /min python combined_testing.py'
        }
    }
    stage('clean environemnt') {
        steps {
            bat 'start /min python clean_environemnt.py'
        }
    }
 }
 post {
        always {
            echo 'One way or another, I have finished'
            cleanWs() /* clean up our workspace */
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