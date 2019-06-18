pipeline {
    agent any
    triggers {
        pollSCM 'H/5 * * * *'
    }
    stages { 
        stage('Maven') {
            steps {
                withMaven(globalMavenSettingsConfig: 'b51ee16d-5e32-4f50-bd3d-460f12460371', maven: 'Maven 3.6.1') {
                    sh 'mvn -DskipTests clean deploy'
                }                
            }
        }
    }
}