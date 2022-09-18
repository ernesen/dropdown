// Jenkins - Dynamic Parametrization | Multi-Option Parameters | Active - Reactive Parameters
// https://www.youtube.com/watch?v=bYi4IXep2mk


pipeline {
    agent any

    parameters {
        choice(
            name: 'ENV', 
            choices: ['dev', 'stg', 'prd'], 
            description: 'select your build env'
        )
        booleanParam(
            name: 'Docker', 
            defaultValue: true, 
            description: 'do you want to build Docker?'
        )
        booleanParam(
            name: 'OpenShift', 
            defaultValue: false, 
            description: 'do you want to build OpenShift?'
        )
        booleanParam(
            name: 'EKS', 
            defaultValue: true, 
            description: 'do you want to build EKS?'
        )
        booleanParam(
            name: 'API_Scan', 
            defaultValue: false, 
            description: 'do you want to build API Scan?'
        )
        booleanParam(
            name: 'API_Checkov', 
            defaultValue: false, 
            description: 'do you want to build API Checkov?'
        )
        password(
            name: 'PASSWORD', 
            defaultValue: '', 
            description: 'Enter a password for PRODUCTION ENVIRONMENT ONLY'
        )
    }

    stages {
        stage('Clone repository') {
            steps {
                /* Let's make sure we have the repository cloned to our workspace */
                checkout scm
            }
        }
        stage('Example') {
            steps {
                if (${params.ENV} == "prd" && ${params.PASSWORD}.length() == 0){
                    println("Enter a password for PRODUCTION ENVIRONMENT")
                    return 1

                }
                sh "echo Choice: ${params.ENV}"
                sh 'echo Choice: $ENV'
            }
        }
    }
}
