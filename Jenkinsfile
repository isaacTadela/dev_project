pipeline {
agent any
stages {
     stage('get user name') {
            steps {
                bat 'echo "${%username%}"'
            }
        }
        stage('test') {
            steps {
                 bat 'echo "hello"'
            }
     }
 }
}
