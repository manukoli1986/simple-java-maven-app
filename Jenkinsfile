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
		timeout(time:1, unit: 'MINUTES')
		timestamps()
	}
// ##############################################################################################################
// ##############################################################################################################	
    stages {
		stage ('Clone') {
			steps {
		    git branch: 'master', credentialsId: 'GithubCred', url: "${gitUrl}"
			}
		}

        stage ('Build') {
            steps {
                sh 'mvn -Dmaven.test.failure.ignore=true install' 
            }
            post {
                success {
                    junit 'target/surefire-reports/**/*.xml' 
                }
            }
        }
        stage ('Unit-Test') {
        	steps {
        		echo "Testing code"
        		sleep 30
        		}
        }
        stage ('Quality-scan') {
        	steps {
        		echo "Sonar Scan"
        		sleep 30
        		}
        }

        stage ('Upload to artifactory') {
        	steps {
        		echo "Nexus"
        		sleep 30
        		}
        }

        
    }
}