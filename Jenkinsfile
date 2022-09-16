pipeline {
    agent any

    stages {
        stage('ci') {
            steps {
                sh 'zip -r index.html-$BUILD_NUMBER.zip *'
                sh 'aws s3 cp index.html-$BUILD_NUMBER.zip s3://rct-vnyk-nagar/'
            }
        }
        stage('cd') {
            steps {
                sh 'aws s3 cp s3://rct-vnyk-nagar/index.html-$BUILD_NUMBER.zip .'
                sh ' unzip index.html-$BUILD_NUMBER.zip'
                sh 'scp index.html root@172.31.4.139:/var/www/html/'
            }
        }
    }
}
