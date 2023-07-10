pipeline {
    agent any
    stages {
        stage("Clone Git Repository") {
            steps {
                git(
                    url: "https://github.com/Rahul-Kumar-Paswan/git-demo-1.git",
                    branch: "main",
                    changelog: true,
                    poll: true
                )
            }
        }
        stage("Create artifacts or make changes") {
            steps {
                sh "touch testfile"
                sh "git add testfile"
                sh "git commit -m 'Add testfile from Jenkins Pipeline'"
            }
        }
        stage("Push to Git Repository") {
            steps {
                withCredentials([gitUsernamePassword(credentialsId: 'git-credentials', gitToolName: 'Default')]) {
                    sh "git push -u origin main"
                }
            }
        }
    }
    post {
        always {
            deleteDir()
        }
    }
}



