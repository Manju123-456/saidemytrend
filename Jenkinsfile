pipeline {
    agent any
 
    environment {
        PATH = "/opt/mvn/bin:$PATH"  // Sets Maven path
    }
 
    stages {
        stage("build") {
            steps {
                sh 'mvn clean deploy'    // Runs your Maven build
            }
        }
 
        stage("SonarQube analysis") {
            environment {
                scannerHome = tool 'SonarScanner'  // SonarScanner tool name
            }
            steps {
                withSonarQubeEnv('sonar-server') {
                    sh "${scannerHome}/bin/sonar-scanner"  // Runs the scanner
                }
            }
        }
    }
}
