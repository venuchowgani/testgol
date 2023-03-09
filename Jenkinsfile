pipeline {
    agent {label 'MAVEN_JDK8'}
    stages {
        stage('giturl') {
            steps {
                git url: 'https://github.com/venuchowgani/testgol.git',
                    branch: 'main'
            }
        }
        stage('package') {
            tools {
                jdk 'JDK_8'
            }
            steps {
                sh 'mvn package'
            }
        }
        stage('post build') {
            steps {
                archiveArtifacts artifacts: '**/target/gameoflife.war',
                                 onlyIfSuccessful: true
                junit testResults: '**/surefire-reports/TEST-*.xml'
            }
        }
    }
}