pipeline{
    agent any 
    stages{
        stage('Build'){
	    when {
	        branch 'feature/*'
	       }
	    steps{
            echo "Building latest code"
        }
    }   
	//Deploy to Nexus artifact for feature branch
        stage('Deploy to Nexus artifact') {
            when {
                branch 'feature/*'
            }
            steps{
                echo "Deploying to feature env"
            }
        }
        stage('Deploy to Dev') {
            when {
                branch 'development'
            }
            steps{
                echo "Deploying to dev env"
            }
        }
        stage('Deploy to staging'){
            when {
                branch 'staging'
            }
            steps{
                echo "Deploying to staging env"
            }
        }
        stage('Deploy to Prod'){
            when {
                branch 'master'
            }
            steps {
                echo "Deploying to Prod env"
            }
        }
}
}
