pipeline {
    agent{
        docker {
            image "server1-image-6562515m"
        }
    }
            
    stages {
        stage('ST1-6562515m') {
            steps {
                echo 'ST1-6562515m: Setup Release Environment Completed'
            }
        }
        stage('ST2-6562515m') {
            steps {
                echo 'ST2-6562515m: Server1 is successfully created'
            }
        }
        stage('ST3-6562515m') {
            steps {
                echo 'ST3-6562515m: Server1 is healthy - health check done'
            }
        }
       stage('ST4-Parallel-6562515m') {
            parallel{
                stage('ST4A-6562515m'){
                steps {
                    sh 'echo "ST4A-6562525m: SQLI Check Completed"'
                    }
                    }
                stage('ST4B-6562515m'){
                steps{
                    sh 'echo "ST4B-6562525m: XSS Check Completed"'
                    }
                    }
            }
        }
        stage('ST5-6562515m') {
                steps {
                    input("Continue the pipeline")
                    echo 'ST5-6562515m: Continue the pipeline' 
                      }
                  }
        stage('ST6-6562515m') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
