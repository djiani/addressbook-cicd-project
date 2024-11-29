pipeline{
    agent any
    stages{
        stage("1. checkout git"){
            steps{
                git url: "https://github.com/NikitasGithub/addressbook-cicd-project.git"
            }
        }
        stage("2. compile the code"){
            steps{
                sh "mvn compile"
            }
        }
        stage("3. Testing of the code"){
            steps{
                sh "mvn test"
            }
        }
        stage("4. qa of the code"){
            steps{
                sh "mvn pmd:pmd"
            }
        }
        stage("5. package"){
            steps{
                sh "mvn package"
            }
        }
       

    }
    
}
