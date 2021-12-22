pipeline{
    agent{
        label "nodejs"
    }
    stages{
        stage("Install dependencies"){
            steps{
                sh "npm ci"
            }
        }

        stage("Check Style"){
            steps{
                sh "npm run lint"
            }
        }

        stage("Test"){
            steps{
                sh "npm test"
            }
        }
	
	stage('Release') {
           steps {
               sh '''
               oc project ravivittal-s2i
               oc start-build greeting-console  --follow --wait
               '''
           }
        }

        // Add the "Deploy" stage here
    }
}
