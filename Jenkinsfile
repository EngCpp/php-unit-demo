pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo "Running  ${currentBuild.fullDisplayName}-${env.BUILD_ID} on ${env.JENKINS_URL}"
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
                sh 'phpunit --bootstrap src/* --testdox tests'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                
                sh 'rm -rf /var/www/html/${currentBuild.fullDisplayName} && mkdir /var/www/html/${currentBuild.fullDisplayName}'                
                sh 'cp src/* /var/www/html/${currentBuild.fullDisplayName}/'
            }
        }
    }
}
