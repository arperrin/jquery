pipeline {
    agent any
    tools {        
        maven 'Maven 3.6.1'
    }
    stages { 
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Publish To Nexus') {            
            steps {
                script {
                    def pom = readMavenPom file: 'pom.xml'
                    def version = pom.version
                    def artifact = "${WORKSPACE}/target/" + pom.artifactId + "-" + pom.version + ".jar"

                    nexusPublisher nexusInstanceId: 'Nexus', 
                        nexusRepositoryId: 'jquery', 
                        packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: 'jar', filePath: "${artifact}"]], 
                        mavenCoordinate: [artifactId: 'jquery', groupId: 'aperrin', packaging: 'jar', version: "${version}"]]]
                }
            }
        }
    }
}