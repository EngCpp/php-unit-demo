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
                
                echo 'rm -rf /var/www/html/${currentBuild.fullDisplayName}'
                sh returnStdout: true, script:'rm -rf /var/www/html/${currentBuild.fullDisplayName}'
                
                echo 'mkdir /var/www/html/${currentBuild.fullDisplayName}'
                sh returnStdout: true, script:'mkdir /var/www/html/${currentBuild.fullDisplayName}'                
                
                echo 'cp src/* /var/www/html/${currentBuild.fullDisplayName}/'
                sh 'cp src/* /var/www/html/${currentBuild.fullDisplayName}/'
            }
        }
    }
}
