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
              withDockerRegistry([credentialsId: "jenkins_token", url: ""]) {
              sh 'printenv'
              sh 'docker build -t sachin0710/sachin-jenkins:""$GIT_COMMIT"" .'
              sh 'docker push sachin0710/sachin-jenkins:""$GIT_COMMIT"".'
            }
           }
        }  
    }
    
}
