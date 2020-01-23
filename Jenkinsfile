#!/usr/bin/env groovy
@Library('jenkins-lib@master')_
import io.abc.*
import jenkins.model.*

pipeline {
    agent any
    tools {
        maven 'Maven 3.3.9'
        jdk 'jdk8'
    }
    stages {
        stage ('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                '''
            }
        }
		stage('Clone'){
			steps {
			git credentialsId: 'GithubCred', url: 'https://github.com/manukoli1986/simple-java-maven-app.git'
			// echo 'This is a minimal pipeline.'
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


pipeline {
	agent any 
	stages {
		stage('Clone'){
			steps {
				// git credentialsId: 'GithubCred', url: 'https://github.com/manukoli1986/simple-java-maven-app.git'
			echo 'This is a minimal pipeline.'
			}
		}
		stage('Build'){
			steps {
				timeout(time: 1, unit: 'seconds') {
					// sh 'mvn clean verify -DSkiptest=True'
					sleep 5
				}
			}
		}
		}
}