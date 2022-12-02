pipeline {
  agent any
    
  tools {nodejs "node"}
    
  stages {
        
    stage('Cloning Git') {
      steps {
        git 'https://github.com/jayasimha537/nodejs-my-app.git'
      }
    }
        
    stage('Install dependencies') {
      steps {
        sh 'npm install'
      }
    }
    
    stage('Stoping Nginx') {
      steps {
        sh 'docker kill nginx'
        sh 'docker rm nginx'
      }
    }
    
     
    stage('Build') {
      steps {
         sh 'npm run build'
      }
    }
    
    stage('Imaging') {
      steps {
         sh 'docker build -t mynginx:1.1 -t mynginx:latest .'
      }
    }
    
    stage('Starting Nginx') {
      steps {
        sh 'docker run -d -p 3000:80 --name nginx mynginx'
      }
    }
    
  }
}
