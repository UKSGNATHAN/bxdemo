pipeline{
    agent any
    options {
            buildDiscarder(logRotator(
                // number of Builds to Keep 
                numToKeepStr:  env.BRANCH_NAME ==~ /master|develop/ ? '3': 
                               env.BRANCH_NAME ==~ /(feature|bugfix|staging|release|hotfix)\/.*/ ? '20' : '5', 
                // number of builds to keep the artifacts from                
                artifactNumToKeepStr:  env.BRANCH_NAME ==~ /master|develop/ ? '3':
                               env.BRANCH_NAME ==~ /(feature|bugfix|staging|release|hotfix)\/.*/ ? '20' : '5'
                                ))
    } 
    stages{
        stage('Build'){
            when {
                branch 'feature/*'
            }
            steps {
                echo "Building latest code"
            }
        }
        stage('Deploy to Feature') {
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
                 expression {
                return env.BRANCH_NAME ==~ /master|development/ ? ;
                 }
            }
            steps {
                echo "Deploying to Prod env"
            }
        }
}
}
