pipeline {
    agent any
    
    stages{
        stage('checkout code'){
            steps {
                    git credentialsId: 'pathelloworld',url: 'https://github.com/Riyouk/hello_python_app.git',branch : 'main'
            }
        }

        stages('install Dependencies') {
            steps{
                bat ''' 
                    python -m venv venv
                    call venv\\Scripts\\activate
                    pip install --upgrade pip
                    pip install -r requierment.txt
                '''
            }
        }

        stage('Run Tests') {
            steps {
                bat '''
                    call venv\\Scripts\\activate 
                    pytest test_hello.py
                    '''

            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying Application...'

                bat '''
                    call nenv\\Scripts\\activate
                    python hello_world.py
                '''
            
            }
        }
    }

    post {
        success {
            echo 'pipeline succeeded'
        }
        failure{
            echo 'pipeline failed!'
        }
    }
}