pipeline{
    agent{
        label{
            label 'slave1'
        }
    }
    tools{
        maven 'maven'
    }
    stages{
        stage('checkout stage'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'jenkinsgit', url: 'https://github.com/Team3-Group6-Engops/projrct11.git']]])
            }
        }
        stage('parallel-slave1'){
          parallel{
            stage('sub stage 1'){
                steps{
                    sh 'whoami'
                }
            }
            stage('sub stage2'){
                steps{
                    sh 'free -m'
                }
            }
          }
        }
        stage('stage for node 2'){
            parallel{
                stage('sub parallel node2'){
                    agent{
                        label{
                            label 'slave3'
                        }
                    }
                    steps{
                        echo "I am a Devops Engineer"
                    }
                }
                stage('sub parallel2 node2'){
                    steps{
                        echo "We shall all get there"
                    }
                    agent{
                        label{
                            label 'slave1'
                        }
                    }
                }
            }
        }
        stage('stage for node 3'){
            
            parallel{
                stage('sub parallel1 node3'){
                    steps{
                        echo "We are now senior Engineers"
                    }
                }
                stage('sub parallel2 node3'){
                    steps{
                        echo "Etech Consulting is great"
                    }
                }
            }
        }
        stage('stage 4'){
            steps{
                sh 'lscpu'
            }
            agent{
                label{
                    label 'slave2'
                }
            }
        }
        stage('stage4 level2'){
            agent{
                label{
                    label 'slave2'
                }
            }
            steps{
                echo 'I believe I can do this'
            }
        }
    }
}