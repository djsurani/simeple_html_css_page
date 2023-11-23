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
          '''
        sh 'pip install -r requirement.txt'
        }
      }
        stage('Deploy') {
            steps {
                git branch: 'main' , url: 'https://github.com/djsurani/simeple_html_css_page.git'
                // Set GCP project
                    sh '''
                    gcloud config set project $CLOUDSDK_CORE_PROJECT
                    
                  gcloud monitoring alert-policies list --filter="conditions.conditionDisplayName='CPU Usage'"
                  '''


            }
    }
}
}
