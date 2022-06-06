def GITHUB_REPO = 'https://github.com/lesstif/laravel-9-jenkins-demo.git'
def workspace = env.WORKSPACE

pipeline {
    agent  any
    stages {
        stage('prepare') {
            steps {
                sh "pwd"
                dir('change-to-deploy-folder') {
                    sh 'cd /var/www/lesstif/opendevops'
                }
                sh "git pull origin main"
            }
        }

        stage('build') {
            steps {
                 sh "pwd"
                dir('change-to-deploy-folder') {
                    sh 'cd /var/www/lesstif/opendevops'
                }
                sh "composer install"
                sh "php artisan cache:clear"
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
