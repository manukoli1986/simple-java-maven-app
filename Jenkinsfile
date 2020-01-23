#!/usr/bin/env groovy
@Library('jenkins-lib@master')_
import io.abc.*
import jenkins.model.*

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