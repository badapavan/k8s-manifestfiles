pipeline {

   agent any 

   stages {
     stage ('checkout') {
       steps {
            git branch: 'main', 
            credentialsId: 'GITHUB-LOGIN-CREDS', 
            url: 'https://github.com/badapavan/Jenkins-Zero-To-Hero.git'
       }
     }
     
     stage ('Build Docker') {
       steps {
         sh 'echo ' build the image''
         sh 'docker build -t "pavankmb/pipeline-ci-cd:${BUILD NUMBER} .'
       }
     }
     
     stage ('Docker Push') {
       steps {
       sh 'echo'push to dockerhub''
       sh ' docker push pavankmb/pipeline-ci-cd:${BUILD NUMBER}'
       }
     }
  
     stage ('checkout k8s manifest scm') {
       steps {
         git branch: 'main', 
         credentialsId: 'GITHUB-LOGIN-CREDS', 
         url: 'https://github.com/badapavan/k8s-manifestfiles.git'
       }
     }

     stage ('update k8s manifest and push to repo') {
       steps {
         sh '''
         cat depoly.yaml
         git add depoly.yaml
         git commit -m " update depoly yaml | jenkinsfile pipeline"
         git push https://github.com/badapavan/k8s-manifestfiles.git HEAD:main
       }
     }
   }
}
