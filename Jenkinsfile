pipeline {
agent any
stages {
stage('Checkout') {
steps {
git 'https://github.com/votre-utilisateur/nom-du-projet.git'
}
}
stage('Build') {
steps {
sh 'docker build -t my-devsecops-app .'
}
}
stage('Test') {
steps {
sh 'docker run -d -p 8080:8080 my-devsecops-app'
sh 'curl http://localhost:8080'
}
}
stage('Clean Up') {
steps {
sh 'docker stop $(docker ps -q)'
}
}
}
}	
