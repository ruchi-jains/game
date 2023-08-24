pipeline {
    agent any
    
    stages {
        stage ('SCM checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/ruchi-jains/game.git'
            }
            
        }
        
        stage ('docker image build') {
            steps {
                sh '/usr/bin/docker image build -t ruchi0118/game .'
            }
        }
        
        stage ('Docker Login') {
            steps {
                sh 'echo dckr_pat_fMfae2shru-71E3CoJBiwZZJ5YI | /usr/bin/docker login -u ruchi0118 --password-stdin'
            }
        }
        
        stage ('docker image Push') {
            steps {
                sh '/usr/bin/docker image push ruchi0118/game'
            }
        }
        
        stage ('remove existing service') {
            steps {
                sh '/usr/bin/docker service rm game'
            }
        }
        
        stage ('create docker service') {
            steps {
                sh '/usr/bin/docker service create --name game -p 80:80 ruchi0118/game'
            }
        }
        
    }
}

