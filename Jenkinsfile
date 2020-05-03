pipeline {
     agent any
     stages {
        stage('Lint HTML') {
            steps {
                sh 'tidy -q -e index.html'
            }
        }                                           
         stage('Upload to AWS') {
             steps {
                 withAWS(region:'us-east-2', credentials:'aws-static')
                  {
                       s3Upload(file:'index.html', bucket:'jenkinsalexrezn')
                  }
                 sh 'echo "Hello World"'
                 sh '''
                     echo "Multiline shell steps works too"
                     ls -lah
                 '''
               }
         }
     }
}
