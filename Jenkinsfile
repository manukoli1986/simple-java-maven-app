#!/usr/bin/env groovy
@Library('jenkins-lib@master')_
import io.abc.*
import jenkins.model.*

pipeline {
    agent any
    tools {
        maven 'maven'
        jdk 'jdk'
    }
    environment {
    	gitUrl = "https://github.com/manukoli1986/simple-java-maven-app.git"
    }
	options {
		timeout(time:5, unit: 'MINUTES')
		buildDiscarder(logRotator(numToKeepStr: '10'))
		timestamps()
	}
// ##############################################################################################################
    stages {
		stage ('Clone') {
			steps {
		    git branch: 'master', credentialsId: 'GithubCred', url: "${gitUrl}"
			}
		}

        stage ('Build') {
        	input {
        		message "Please click if you're ready"
        		ok "OK"
        	}
            steps {
                sh 'mvn -Dmaven.test.failure.ignore=true install' 
            }
            post {
                success {
                    junit 'target/surefire-reports/**/*.xml' 
                }
            }
        }
        // stage ('Unit-Test') {
        // 	steps {
        // 		echo "Testing code"
        // 		sleep 30
        // 		}
        // }
        // stage ('Quality-scan') {
        // 	steps {
        // 		echo "Sonar Scan"
        // 		sleep 30
        // 		}
        // }

        // stage ('Upload to artifactory') {
        // 	steps {
        // 		echo "Nexus"
        // 		sleep 30
        // 		}
        // }
        stage ('Deploy') {
            when { tag pattern: "v1\\d+", comparator: "REGEXP"}
            steps {
                echo 'Deploying only because this commit is tagged...'
                // sh 'make deploy'
            }
        }
	}
}