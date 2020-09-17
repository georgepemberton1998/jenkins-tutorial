pipeline{
        agent any
        stages{
            stage('Clone repo'){
                steps{
                    sh "git clone https://gitlab.com/qacdevops/chaperootodo_client && cd chaperootodo_client"
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
                    sh "pwd && ls -la && sudo docker-compose up -d"
                }
            }
        
        }    
}
