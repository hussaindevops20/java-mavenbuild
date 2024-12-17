pipeline {
    agent any

    tools {
        maven "maven"
    }
    options { 
        timestamps()
            }
    parameters { string(name: '$branch', defaultValue: 'main', description: '') }
    stages {
        stage('Maven Build') {
            steps {
                   sh 'mvn clean package'
            }
        }    
    }     
    post {
        success {
                    junit '**/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'target/*.jar'
            }
        }

    }
