pipeline {
    agent any
    stages { 
        stage ('Checkout') {
          steps {
            git 'https://www.github.com/arperrin/jquery.git'
          }
        }
        stage('Maven') {
            steps {
                withMaven(globalMavenSettingsConfig: 'b51ee16d-5e32-4f50-bd3d-460f12460371', maven: 'Maven 3.6.1') {
                    sh 'mvn -DskipTests clean deploy'
                }                
            }
        }
    }
}