pipeline {
    agent any
    stages {
        
        stage('checkout'){
            steps {
                checkout scm }
        }
        stage('git') {
            steps {
                  git branch: 'main', url : 'https://github.com/Sayfez/TpDevops.git'}
                  }
      stage('Construction') {
            steps {
                // Exécuter votre processus de construction (par exemple, Maven, Gradle, etc.)
                sh 'mvn clean package'
            }
        }
          
        stage('Tests') {
            steps {
                // Exécuter vos tests unitaires ou tests d'intégration
                sh 'mvn test'
            }
             post {
        failure {
            script {
                emailext(
                    subject: "Pipeline Failed: ${currentBuild.fullDisplayName}",
                    body: "The pipeline has failed. Please check the console output for details.",
                    to: 'djsayf16@gmail.com',
                    attachLog: true,
                )
            }
        }
        
        success {
            script {
                emailext(
                    subject: "Pipeline Succeeded: ${currentBuild.fullDisplayName}",
                    body: "The pipeline has succeeded. You can view the results at ${BUILD_URL}",
                    to: 'djsayf16@gmail.com',
                    attachLog: true,
                )
            }
        }
    }
}

        
       stage('sonarqube') {
           steps {
           withSonarQubeEnv('sonarserver') {
                                      sh 'mvn sonar:sonar -Dsonar.java.binaries=target/classes'}
           }
       }

        
        stage('Nexus') {
                           
            steps {
              sh 'mvn deploy'
            }
               
            }
               stage("docker image"){
            steps {
                  {
                script{
                    sh 'docker build -t devops . '
                    sh'docker tag devops sayfez/devops'

                }}
               
            }
           
        } 
        
       
        //
      // stage('Déploiement') {
      //       steps {
      //           // Déployer votre application sur un serveur ou une plateforme spécifique
      //           sh 'mvn deploy'
      //       }
      //   }
    }
}
