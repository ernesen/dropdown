// Jenkins - Dynamic Parametrization | Multi-Option Parameters | Active - Reactive Parameters
// https://www.youtube.com/watch?v=bYi4IXep2mk



// properties([
//   parameters([
//     [
//       $class: 'ChoiceParameter',
//       choiceType: 'PT_SINGLE_SELECT',
//       name: 'Environment',
//       script: [
//         $class: 'ScriptlerScript',
//         scriptlerScriptId:'Environments.groovy'
//       ]
//     ],
//     [
//       $class: 'CascadeChoiceParameter',
//       choiceType: 'PT_SINGLE_SELECT',
//       name: 'Host',
//       referencedParameters: 'Environment',
//       script: [
//         $class: 'ScriptlerScript',
//         scriptlerScriptId:'HostsInEnv.groovy',
//         parameters: [
//           [name:'Environment', value: '$Environment']
//         ]
//       ]
//    ]
//  ])
// ])

// pipeline {
//   agent any
//   stages {
//     stage('Clone repository') {
//         /* Let's make sure we have the repository cloned to our workspace */
//         checkout scm
//     }

//     stage('Build') {
//       steps {
//         echo "${params.Environment}"
//         echo "${params.Host}"
//       }
//     }
//   }
// }
def type = true
pipeline {
    agent any
    if (type){ 
        parameters {
            password(
                name: 'PASSWORD', 
                defaultValue: '', 
                description: 'Enter a password for production environment only'
            )
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
    } else {
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
                echo "Choice: ${params.ENV}"
                sh "echo Choice: ${params.ENV}"
                sh 'echo Choice: $ENV'
            }
        }
    }
}
