pipeline {
agent any
tools {
maven 'maven'
}
stages {
stage('Git Checkout') {
steps {
git branch: 'main',
credentialsId: 'b43c15d0-7df1-4e0c-bd5e-d0ca7a287179',
url: 'https://github.com/navneetguraya/sonar.git'
}
}
  stage('SonarQube analysis') {
    def scannerHome = tool 'sonarqube';
    withSonarQubeEnv('sonarqube') {
      sh "${scannerHome}/bin/sonar-scanner \
      -D sonar.login=admin \
      -D sonar.password=admin \
      -D sonar.projectKey=sonarqubetest \
      -D sonar.exclusions=vendor/**,resources/**,**/*.java \
      -D sonar.host.url=http://192.168.1XX.XX:9000/"
    }
  }
}
}
