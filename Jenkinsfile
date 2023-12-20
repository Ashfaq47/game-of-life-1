pipeline {
    agent { label 'Maven || JDK_8' }
    tools {
        jdk 'JDK_8'
        maven 'Maven_3.9.6'
    }
    options {
        timeout(time: 15, unit: 'MINUTES')
    }
    triggers {
        pollSCM('* * * * *')
    }
    stages {
        stage("git") {
            steps {
                 git url: 'https://github.com/Ashfaq47/game-of-life-1.git' ,
                    branch: 'dev'
            }
        }
        stage("build") {
            steps {
                sh 'mvn clean package'
                archiveArtifacts artifacts: '**/gameoflife-*.jar'
                junit testResults: '**/TEST-*.xml'
            }
        }
    }
}