def GITHUB_REPO = 'https://github.com/lesstif/laravel-9-jenkins-demo.git'
def workspace = env.WORKSPACE

pipeline {
    agent  any
    stages {
        stage('prepare') {
            steps {
                sh 'echo "Hello World"'
                sh '''
                echo "Multiline shell steps works too"
                ls -lah
                '''
                sh 'cd /var/www/lesstif/opendevops'
                sh 'pwd'
            }
        }

        stage('build') {
            steps {
                sh 'pwd'
                echo  'build done'
            }
        }

        stage('deployments') {
            parallel {
                stage('deploy to stg') {
                    steps {
                        echo 'stg deployment done'
                    }
                }
                stage('deploy to prod') {
                    steps {
                        echo 'prod deployment done'
                    }
                }
            }
        }
    }
}
