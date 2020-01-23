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
    stages {
		stage ('Clone') {
			options {
        		timeout(time:10, unit: 'MINUTES')
        	}
			steps {
		    git branch: 'master', credentialsId: 'GithubCred', url: 'https://github.com/manukoli1986/simple-java-maven-app.git'
			}
		}

        stage ('Build') {
        	options {
        		timeout(time:10, unit: 'MINUTES')
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
    }
}