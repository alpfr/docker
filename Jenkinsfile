node {
    def app

    stage('Clone repository') {
      

        checkout scm
    }

    stage('Build image') {
  
       app = docker.build("adetolaadesanya/test")
    }

    stage('Test image') {
  

        app.inside {
            sh 'echo "Tests passed now"'
        }
    }

    stage('Push image to the docker registry') {
        
        docker.withRegistry('https://registry.hub.docker.com', 'hubregistery') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }
}
