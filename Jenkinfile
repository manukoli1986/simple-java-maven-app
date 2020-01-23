#!/usr/bin/env groovy
@Library('jenkins-lib@master')_
import io.abc.*
import jenkins.model.*

node('master'){
    
    stage('Clone'){
        git credentialsId: 'GithubCred', url: 'https://github.com/manukoli1986/simple-java-maven-app.git'
    }
    stage('Build'){
        sh 'mvn clean verify -DSkiptest=True'
        //mvnBuild("mvn")
    }
}
