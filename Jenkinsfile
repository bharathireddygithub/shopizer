    pipeline {
        agent {label 'node'}

        stages {
            stage ('git') {
                steps {
                    git branch: 'master', 
                    url: 'https://github.com/bharathireddygithub/shopizer.git'
                } 
     
            }
            stage ('build') {
                steps {
                    sh 'mvn package'
                }
            }   
            stage ('artifactory') {
                 steps {
                        archiveArtifacts artifacts: '**/target/*.jar'
                    }
                }
            stage ('test reports') {
                 steps {
                        junit '**/target/surefire-reports/*.xml'
                    }
                }

        }
    }
