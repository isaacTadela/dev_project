pipeline {
agent any
stages {
    stage('pull from git') {
        steps {
            git 'clone https://github.com/isaacTadela/dev_project'
        }
    }
    stage('run servers') {
        steps {
            bat 'start /min python rest_app.py'
        }
        steps {
            bat 'start /min python web_app.py'
        }
    }
    stage('_testing') {
        steps {
            bat 'start /min python backend_testing.py'
        }
        steps {
            bat 'start /min python frontend_testing.py'
        }
        steps {
            bat 'start /min python combined_testing.py'
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

// Pull code from your Github repository holding your previous project (part 1).
// 2. Run rest_app.py (backend)
// 3. Run web_app.py (frontend)
// 4. Run backend_testing.py
// 5. Run frontend_testing.py
// 6. Run combined_testing.py
// 7. Run clean_environemnt.py
