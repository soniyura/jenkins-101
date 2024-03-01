pipeline {
    agent {
        node {
            label 'docker-agent-python'
            }
      }
    triggers {
        pollSCM '* * * * *'
    }
    stages {
        stage('Build') {
            steps {
                echo "Building.."
                sh '''
                echo "========== start install  requirements.txt =========="
                cd myapp
                pip install -r requirements.txt
                echo "=========== end install  requirements.txt ==========="
                '''
            }
        }
        stage('Test') {
            steps {
                echo "Testing.."
                sh '''
                echo "================== start hello.py ==================="
                cd myapp
                python3 hello.py
                echo "=========== start hello.py and add name =============="
                python3 hello.py --name=SONI
                echo "=========== end hello.py and  name =============="
                '''
            }
        }
        stage('Deliver') {
            steps {
                echo 'Deliver....'
                sh '''
                echo "doing delivery stuff.."
                '''
            }
        }
    }
}