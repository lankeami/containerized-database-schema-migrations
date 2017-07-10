node {
  checkout scm
  stage('Build') {
    sh 'docker-compose up -d db'
  }
  stage('Verify') {
    sh 'docker-compose run --rm flyway-info'
  }
  stage('Deploy') {
    sh 'docker-compose run --rm flyway-migrate'
  }
  stage('Verify Again') {
    sh 'docker-compose run --rm flyway-info'
  }
  stage('Clean Up') {
    sh 'docker-compose stop'
    sh 'docker-compose down --volumes'
  }
}
