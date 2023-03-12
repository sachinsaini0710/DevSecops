pipeline {
  agent any

  stages {
      stage('Build Artifact Maven') {
            steps {
              sh "mvn clean package -DskipTests=true"
              archive 'target/*.jar' //so that they can be downloaded later
            }
        }  
    stage('Unit-Test') {
            steps {
              sh "mvn test"
            }
        }   
     stage('Docker-file') {
            steps {
              sh 'printenv'
              sh 'docker build -tag "sachin0710/Sachin-jenkin-image:""$GIT-COMMIT"".'
              sh 'docker push "sachin0710/Sachin-jenkin-image:""$GIT-COMMIT"".'
            }
        }  
    }
    
}
