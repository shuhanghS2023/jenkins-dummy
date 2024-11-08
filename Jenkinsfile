pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  stages {

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv(installationName:"SonarQube") {
                    // Run SonarQube scan using sonar-scanner
                    sh """
                    sonar-scanner \
                        -Dsonar.projectKey="jenkins-dummy"} \
                        -Dsonar.projectName="jenkins-dummy" \
                        -Dsonar.python.version=3.8 \
                        -Dsonar.coverageReportPaths=coverage.xml
                        -Dsonar.login="admin"
                        -Dsonar.password="admin"
                    """
                }
            }
        }
  }
}
