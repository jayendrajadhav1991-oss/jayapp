pipeline {
    agent any
    tools { 
        nodejs "nodejs"
        }
    stages {
        stage("Checkout") {
            steps {
                    checkout scm
            }
        }
        stage("install packages") {
            steps {
                bat "npm ci"
            } 

        }
        stage("test") {
            steps{
                // bat "npx ng text --no-watch --no-progress --browser=Chromeheadless"
                echo "testing"
            }
        }
        stage("Build") {
            steps {
                 bat "npx ng build --configuration production"
            }
        }

        stage ("deployment") {
            steps {
                bat "del /q /s C:\inetpub\wwwroot\jayapp\\*"
            bat "xcopy /E /Y /I dist\\newangular\\browser\\* c:\\inetpub\\wwwroot\\jayapp\\"
             } 
        }


    }
    post {
        success {
            echo "Angular application build succesfully"
        } 
        failure {
            echo "angular build fail"
       }
    } 
    
}

