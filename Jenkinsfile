pipeline {
    agent any
    stages {
        stage('Lint HTML') {
            steps {
                sh 'tidy -q -e *.html'
            }
        }

        stage('Upload to AWS') {
            steps {
                withAWS(credentials: 'aws-credentials', region: 'us-west-2') {
                    sh 'echo "Hello World"'
                    sh '''echo "Multiline shell steps work too"
                    ls -lah
                    '''
                    s3Upload 'jenkins-bucket'
                    }
                }
            }

  }
}
