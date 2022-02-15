
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

			  sh 'cd ../../ecsdemo-frontend/kubernetes'
			  sh 'kubectl apply -f frontenddeployment.yaml'
			  sh 'kubectl apply -f frontendservice.yaml'

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