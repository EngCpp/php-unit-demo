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
                def fname = '/var/www/html/${currentBuild.fullDisplayName}'
                
                def exists = new File(fname).exists()
                
                if( exists )
                  sh 'rm ${fname} -rf'
                
                sh 'mkdir /var/www/html/${currentBuild.fullDisplayName}'                
                sh 'cp src/* /var/www/html/${currentBuild.fullDisplayName}/'
            }
        }
    }
}
