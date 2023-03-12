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
              docker.withRegistry( <docker-cred>)
              sh 'printenv'
              sh 'docker build -t sachin0710/sachin-jenkin:""$GIT_COMMIT"" .'
              sh 'docker push sachin0710/sachin-jenkin:""$GIT_COMMIT"".'
            }
        }  
    }
    
}
