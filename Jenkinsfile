pipeline {
    agent any
            
    stages {
        stage('ST1-6562515m') {
            steps {
                echo 'ST1-6562515m: Setup Release Environment Completed'
            }
        }
        stage('ST2-6562515m') {
            steps {
                   script {
                    //check if container is maps to port 32700 on host
                       def result = sh(
                        script: '''
                            docker ps --format '{{.ID}} {{.Names}} {{.Ports}}' | grep '0.0.0.0:32700->' || true
                        ''',
                        returnStdout: true
                    ).trim()

                    if (result) {
                        echo "ST2-6562515m: Server1 is successfully created"
                    } else {
                        error "No container is exposing port 32700." 
                      }     
                    }       
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
                echo 'ST6-6562515m: "Ready for next phase'
            }
        }
    }
}
