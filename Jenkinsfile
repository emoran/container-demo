import jenkins.model.*;
import hudson.plugins.ec2.*;
import groovy.json.*
 
pipeline {
    agent any
 
    stages {
        stage('Build Package') {
            steps {
             
               script {
                    USER = sh(script: 'whoami', , returnStdout: true).trim()
                    sh 'mvn -DskipTests clean package -Pconf -Ddir=/home/${USER}/helloApp'  //helloApp can be any name for directory just make sure to keep it consistent in complete file
                }
            }
        }
        stage('Docker') {
            steps {
               script {
                sh 'docker cp /home/${USER}/helloApp/*.jar mule-cont:/opt/mule-enterprise-standalone-4.1.5/apps'   
                }
            }
        }
    }


}