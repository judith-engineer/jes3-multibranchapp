pipeline{
    agent any
    stages{
        stage('git clone'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'github-id', url: 'https://github.com/judith-engineer/jes3-multibranchapp.git']]])
            }
        }
        stage('parallel-level'){
            parallel {
                stage('sub-job'){
                    steps{
                        echo "sub-job1 task"
                    }
                }
                stage('sub-job2'){
                    steps{
                        echo "sub-job2 task"
                    }
                }
                stage('user-check1'){
                    steps{
                        sh 'cat/etc/passwd | grep jenkins'
                    }
                }
            }
        }
        stage('version-check'){
            steps{
                echo "end of parallel job"
            }
        }
        stage('webhook-fix'){
            steps{
                echo "webhook fix"
            }
        }
       
           }
           
}
