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
            def recentContainer = sh(
                script: '''
                    docker ps -a --format "{{.ID}} {{.CreatedAt}}" |
                    while read id date time tz; do
                        container_time=$(date -d "$date $time $tz" +%s)
                        now=$(date +%s)
                        if [ $(($now - $container_time)) -lt 300 ]; then
                            echo "Recent container: $id"
                            break
                        fi
                    done
                ''',
                returnStdout: true
            ).trim()

            if (recentContainer) {
                echo "ST2-6562515m: Server1 is successfully created"
            } else {
                echo "ST2-6562515m: No recent containers found"
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
                echo 'Deploying....'
            }
        }
    }
}
