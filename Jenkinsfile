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
    environments{
    	gitUrl = "https://github.com/manukoli1986/simple-java-maven-app.git"
    }
	options {
		timeout(time:10, unit: 'MINUTES')
		timestamps()
	}
// ##############################################################################################################
// ##############################################################################################################	
    stages {
		stage ('Clone') {
			steps {
		    git branch: 'master', credentialsId: 'GithubCred', url: ${gitUrl}
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
    }
}