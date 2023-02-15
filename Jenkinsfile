pipeline {
    // 스테이지 별로 다른 거
    agent any

    triggers {
        pollSCM('*/3 * * * *')
    }

    stages {
        // 레포지토리를 다운로드 받음
        stage('Git Pull') {
            agent any
            
            steps {
                echo 'Clonning Repository'

                git url: 'https://github.com/du-du-zi/jenkins_test.git',
                    branch: 'master',
                    credentialsId: 'gittest'
            }

            post {
                // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
                success {
                    echo 'Successfully Cloned Repository'
                }

                always {
                  echo "i tried..."
                }

                cleanup {
                  echo "after all other post condition"
                }
            }
        }
        
        stage('Done msg') {
          agent any

          steps {
            echo 'Test Done"
          }
        }
    }
}
