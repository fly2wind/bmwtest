pipeline {
    agent {
        docker { 
          image 'maven:3.5-jdk-7'
          args '-v $HOME/.m2:/root/.m2'
        }
    }
    stages {
        stage('CHECKOUT') { 
            steps {
                git "https://github.com/fly2wind/bmwtest.git"
            }
        }
        stage('PACKAGE') { 
            steps {
                sh 'mvn clean package -DskipTests=true'
            }
        }
        stage('TEST') { 
            steps {
                sh 'mvn test'
                junit 'reports/**/*.xml' 
            }
        }
    }
}
