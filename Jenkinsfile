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
                
                if [ -d '/var/www/html/${currentBuild.fullDisplayName}' ]; then
                   sh 'rm /var/www/html/${currentBuild.fullDisplayName} -rf' 
                fi
                
                sh 'mkdir /var/www/html/${currentBuild.fullDisplayName}/'
                sh 'cp src/* /var/www/html/${currentBuild.fullDisplayName}/'
            }
        }
    }
}
