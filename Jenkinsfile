pipeline {
    agent any
    environment {
    CLOUDSDK_CORE_PROJECT='formal-cascade-405222'
    GCLOUD_CREDS=credentials('gcloud-creds')
  }
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
    stage('test') {
      steps {
        sh '''
            gcloud version
            gcloud auth activate-service-account --key-file="$GCLOUD_CREDS"
            gcloud compute zones list
          '''
        }
      }
        stage('Deploy') {
            steps {
                git 'https://github.com/djsurani/simeple_html_css_page.git'
            }
    }
}
}
