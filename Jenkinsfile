pipeline {
    agent { label 'my-agent' }

    stages {
        stage('Capture PID') {
            steps {
                sh '''
                    my_command &
                    my_pid=$!
                    echo $my_pid > pid.txt
                '''
            }
        }

        stage('Loop over PIDs') {
            steps {
                script {
                    pids = readFile('pid.txt').trim().split('\n')
                    for (pid in pids) {
                        // Perform actions with the PID, e.g., check status, kill, etc.
                        echo "PID: $pid"
                    }
                }
            }
        }
    }
}