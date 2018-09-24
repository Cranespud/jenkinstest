pipeline {
    agent any

    triggers {
         pollSCM('*/1 * * * *')
     }

stages{
        stage('Build'){
            steps {
                sh 'echo "building"'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/*.php'
                }
            }
        }

        stage ('Deployments'){
            parallel{
                stage ('Deploy to Staging'){
                    steps {
                        sh "cp -i holamundo.php /var/www/html/my-project"
                    }
                }
            }
        }
    }
}
