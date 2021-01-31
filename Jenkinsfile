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
            deleteDir() /* clean up our workspace */
        }
    }
 }

}