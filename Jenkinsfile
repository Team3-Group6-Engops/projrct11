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
        stage('Running on slave1'){
          parallel{
            stage('sub slave1'){
                steps{
                    sh 'whoami'
                }
            }
            stage('sub slave1-2'){
                steps{
                    sh 'free -m'
                }
            }
          }
        }
        stage('Running on slave2'){
            parallel{
                stage('sub slave2'){
                    agent{
                        label{
                            label 'slave2'
                        }
                    }
                    steps{
                        echo "I am a Devops Engineer"
                    }
                }
                stage('sub slave2-2'){
                    steps{
                        echo "We shall all get there"
                    }              
                }
            }
        }
        stage('Running on slave2'){
            parallel{
                stage('sub slave2'){
                    steps{
                        echo "We are now senior Engineers"
                    }
                }
                stage('sub node2-2'){
                    steps{
                        echo "Etech Consulting is great"
                    }
                }
            }
        }
        stage('stage 4 slave3'){
            agent{
                label{
                    label 'slave3'
                }
            }
            steps{
                sh 'lscpu'
            }
        }
        stage('stage4 slave3-2'){
            steps{
                echo 'I believe I can do this'
            }
        }
    }
}