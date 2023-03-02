pipeline {
    agent any 
    stages{
        stage('BUILD') {
            when {
                branch 'master'
            }
            steps{
                 sh '''
                    sleep 5
                    echo "This is a BUILD stage"
                '''
            }
        }

        stage('TEST') {
            when {
                branch 'master'
            }
            steps{
                sh '''
                    sleep 6
                    echo "This is a TEST stage"
                '''
            }
        }

        stage('DEPLOY') {
            when {
                branch 'master'
            }
            steps{
                sh '''
                    sleep 5
                    echo "This is a DEPLOY stage"
                '''
            }
        }
        stage('POST BUILD') {
            when {
                branch 'master'
            }
            steps{
                sh 'echo "This is a POST BUILD stage"'  
            }
        }   
    }
}
