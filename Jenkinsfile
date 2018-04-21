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
                File folder = new File("/var/www/html/${currentBuild.fullDisplayName}")
                
                if( folder.exists() )
                    folder.deleteDir() 
                
                folder.mkdirs()
                
                sh 'cp src/* /var/www/html/${currentBuild.fullDisplayName}/'
            }
        }
    }
}
