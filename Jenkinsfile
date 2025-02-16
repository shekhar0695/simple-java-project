pipeline {
    agent any
    parameters {
        string defaultValue: 'main', name: 'BRANCH', trim: true
    }
    environment {
        BRANCH_NAME = "${BRANCH}"
    }    
    stages {
        stage('BUILD') {
            steps{
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    sh '''
                        sleep 5
                        echo "This is a BUILD stage $BRANCH_NAME"
                        exit 1
                    '''
                }
            }
        }

        stage('TEST') {
            parallel {

                stage('TEST ON LINUX MACHINE') {
                    steps {
                        sh '''
                            sleep 6
                            echo "This is a TEST on LINUX"
                            exit 1
                        '''
                    }
                }

                stage('TEST ON WINDOWS MACHINE') {
                    steps {
                        sh '''
                            sleep 6
                            echo "This is a TEST on WINDOWS"
                        '''
                    }
                }

                stage('TEST ON MAC MACHINE') {
                    steps {
                        catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                            sh '''
                                sleep 6
                                echo "This is a TEST on WINDOWS"
                                exit 1
                            '''
                        }    
                    }
                }

                stage('TEST ON CHROME MACHINE') {
                    steps {
                        sh '''
                            sleep 6
                            echo "This is a TEST on WINDOWS"
                        '''
                    }
                }

            }
        }

        stage('DEPLOY') {
            steps{
                sh '''
                    sleep 5
                    echo "This is a DEPLOY stage $BRANCH_NAME"
                '''
            }
        }
    }

    post {

        always {
            echo "This will run always"
        }

        success {
            echo "This $JOB_NAME SUCCESS - $BUILD_NUMBER $BUILD_ID $BUILD_DISPLAY_NAME"
        }

        unstable {
            echo "This $JOB_NAME UNSTABLE - $BUILD_NUMBER $BUILD_ID $BUILD_DISPLAY_NAME"
        }

        failure {
            echo "This $JOB_NAME FAILED - $BUILD_NUMBER $BUILD_ID $BUILD_DISPLAY_NAME"
        }

    }
}
