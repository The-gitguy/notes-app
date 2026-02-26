/**
 * Imports the shared library for Jenkins pipeline.
 * 
 * The 'Shared' library contains reusable pipeline code, functions, and variables
 * that can be utilized across multiple Jenkinsfile definitions.
 * 
 * The underscore (_) suffix indicates that this library is being loaded without
 * specifying a version, so it will use the default version configured in Jenkins.
 * 
 * Usage: This statement must appear at the beginning of the Jenkinsfile before
 * any pipeline code that references functions or variables from the shared library.
 */
@Library('Shared')_
pipeline{
    agent { label 'dev-server'}
    
    stages{
        stage("Code clone"){
            steps{
                sh "whoami"
            clone("https://github.com/LondheShubham153/django-notes-app.git","main")
            }
        }
        stage("Code Build"){
            steps{
            dockerbuild("notes-app","latest")
            }
        }
        stage("Push to DockerHub"){
            steps{
                dockerpush("dockerHubCreds","notes-app","latest")
            }
        }
        stage("Deploy"){
            steps{
                deploy()
            }
        }
        
    }
}
