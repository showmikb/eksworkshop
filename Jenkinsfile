
pipeline{

	agent any

	
	stages {

		

        stage('eks deploy') {

			steps {
			  sh 'ls ecsdemo-nodejs/'
			  sh 'aws eks update-kubeconfig --region us-west-1 --name demo'
			  sh 'kubectl apply -f ecsdemo-nodejs/kubernetes/deployment.yaml'
			  sh 'kubectl apply -f ecsdemo-nodejs/kubernetes/service.yaml'

			  sh 'kubectl apply -f ecsdemo-crystal/kubernetes/deployment.yaml'
		 	  sh 'kubectl apply -f ecsdemo-crystal/kubernetes/service.yaml'

			  sh 'cd ../../ecsdemo-frontend/kubernetes'
			  sh 'kubectl apply -f ecsdemo-frontend/kubernetes/deployment.yaml'
			  sh 'kubectl apply -f ecsdemo-frontend/kubernetes/service.yaml'

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