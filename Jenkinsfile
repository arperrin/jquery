pipeline {
    agent any
    tools {        
        maven 'Maven 3.6.1'
    }
    stages { 
        stage('Build') {
            steps {
                sh'''
                    mvn clean package
                '''
            }
        }
        stage('Publish To Nexus') {
            steps {
                nexusPublisher nexusInstanceId: 'Nexus', 
                    nexusRepositoryId: 'jquery', 
                    packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: 'jar', filePath: 'target/jquery.jar']], 
                    mavenCoordinate: [artifactId: 'jquery', groupId: 'aperrin', packaging: 'jar', version: '3.3.1-2-SNAPSHOT']]]
            }
        }
    }
}