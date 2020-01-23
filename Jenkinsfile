#!/usr/bin/env groovy
@Library('jenkins-lib@master')_
import io.abc.*
import jenkins.model.*

pipeline {
	agent any('master') 
	stages {
		stage('Clone'){
			// git credentialsId: 'GithubCred', url: 'https://github.com/manukoli1986/simple-java-maven-app.git'
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