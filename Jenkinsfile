
pipeline{

	agent any

	
	stages {

		

        stage('eks deploy') {

			steps {
			  sh 'aws eks update-kubeconfig --region us-west-1 --name demo'
			  sh 'kubectl apply -f nodejsdeployment.yaml'
			  sh 'kubectl apply -f nodejsservice.yaml'

			  sh 'kubectl apply -f crystaldeployment.yaml'
		 	  sh 'kubectl apply -f crystalservice.yaml'

			
			  sh 'kubectl apply -f frontenddeployment.yaml'
			  sh 'kubectl apply -f frontendservice.yaml'
			  sh '''ELB=$(kubectl get service ecsdemo-frontend -o json )'''

			  sh 'curl -m3 -v $ELB'


			}
		}
	}

	post {
		always {

            		cleanWs()
			
            		echo "done"
		}
	}

}