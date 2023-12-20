pipeline {
    agent any
    tools { 
        jdk 'JDK_8'
        maven 'MAVEN_3.9.6'
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
            }
        }
    }
}