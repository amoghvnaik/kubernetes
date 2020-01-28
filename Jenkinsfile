pipeline{
        agent any
        
        stages{
		stage('--building--'){
			steps{
				sh '''. ~/.bashrc
				      docker-compose build
				      docker-compose push
				      '''
			}
		}
                stage('--deployment--'){
                        steps{
				sh '''. ~/.bashrc
				      sed "s/{{BUILD}}/${BUILD_NUMBER}/g;s/{{MYSQL_USER}}/${MYSQL_USER}/g;s/{{MYSQL_PASSWORD}}/${MYSQL_PASSWORD}/g;s/{{MYSQL_IP}}/${MYSQL_IP}/g;s/{{MYSQL_DB}}/${MYSQL_DB}/g;s/{{MYSQL_KEY}}/${MYSQL_KEY}/g" ./myapp.yaml | kubectl apply -f ./nginx.yaml -f -
                                      '''
                        }
                }
        }
}
