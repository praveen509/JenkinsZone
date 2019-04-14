node {

    stages{

        stage('Pull Repo'){
            steps {
                git 'https://github.com/praveen509/PraveenTestProject.git'
                
            }
        }

        stage('Build'){
            steps {
                bat label: '', script: 'mvn package'
            }
        }

        stage('Publish'){
            steps{
                junit 'target/surefire-reports/*.xml'
            }
            
        }
    }
    

    post {
        success {
          emailext(
            subject: "${env.JOB_NAME} [${env.BUILD_NUMBER}] Development Promoted to Master",
            body: """<p>'${env.JOB_NAME} [${env.BUILD_NUMBER}]' Development Promoted to Master":</p>
            <p>Check console output at &QUOT;<a href='${env.BUILD_URL}'>${env.JOB_NAME} [${env.BUILD_NUMBER}]</a>&QUOT;</p>""",
            to: "praveenreddy.vits@gmail.com"
          )
        }
   
        failure {
        emailext(
            subject: "${env.JOB_NAME} [${env.BUILD_NUMBER}] Failed!",
            body: """<p>'${env.JOB_NAME} [${env.BUILD_NUMBER}]' Failed!":</p>
            <p>Check console output at &QUOT;<a href='${env.BUILD_URL}'>${env.JOB_NAME} [${env.BUILD_NUMBER}]</a>&QUOT;</p>""",
            to: "praveenreddy.vits@gmail.com"
        )
        }
  }
    
}
