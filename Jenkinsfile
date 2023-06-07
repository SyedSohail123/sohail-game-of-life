pipeline {
    agent { label 'MAVEN_JDK8' }
    tools {
        jdk 'JDK_8_UBUNTU'
    }
    stages {
        stage('Version Control') {
            steps {
                git url: 'https://github.com/SyedSohail123/sohail-game-of-life.git',
                    branch: 'declarative'
            }
        }
        stage('Building Package') {            
            steps {
                sh 'mvn package'
            }
        }
        stage('Post build Steps') {
            steps {
                archiveArtifacts onlyIfSuccessful: true,
                                 artifacts: '**/target/gameoflife.war'
                junit testResults: '**/surefire-reports/TEST-*.xml'
            }
        }
    }
}