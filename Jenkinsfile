pipeline{
        agent any
        stages{
            stage('Clone repo'){
                steps{
                    sh '''
                    chmod +x clone-repo.sh
                    ./clone-repo.sh
                    cd chaperootodo_client/"
                }
            }
            stage('install docker and docker compose'){
                steps{
                    sh '''
                    curl https://get.docker.com | sudo bash
                    sudo usermod -aG docker $(whoami)
                    sudo curl -L https://github.com/docker/compose/releases/download/1.21.2/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
                    sudo chmod +x /usr/local/bin/docker-compose
                    '''
                }
            }
            stage('Deploy application'){
                steps{
                    sh "cd chaperootodo_client/ && sudo docker-compose up -d"
                }
            }
        
        }    
}
