pipeline {
    agent any
    tools{
        maven "maven_3_99"
    }

    stages {
        stage('clone repo') {
            steps {
                echo 'This is stage1'
                git 'https://github.com/djiani/addressbook-cicd-project.git'
            }
        }
        
        stage('compile') {
            steps {
                echo 'This is stage2'
                sh 'mvn compile'
            }
        }
        stage('code review') {
            steps {
                echo 'This is stage3'
                sh 'mvn pmd:pmd'
            }
            post{
                success{
                    recordIssues sourceCodeRetention: 'LAST_BUILD', tools: [pmdParser(pattern: '**/pmd.xm')]
                }
            }
        }
        stage('test') {
            steps {
                echo 'This is stage 4'
                sh 'mvn test'
            }
            post{
                success{
                    junit stdioRetention: '', testResults: 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('package') {
            steps {
                echo 'This is stage 5'
                sh 'mvn package'
            }
           
        }
       stage('deploy') {
            steps {
                echo 'This is stage 6'
                sh 'mv /var/lib/jenkins/workspace/mypipilinefromscm/target/*.war  /opt/apache-tomcat-9.0.97/webapps/'
            }
           
        }
    }
    
   
}
