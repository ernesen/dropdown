

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

pipeline {
    agent any
    parameters {
        choice(
            name: 'CHOICE',
            choices: ['one', 'two', 'three'],
            description: ''
        )
    }
    stages {
        stage('Clone repository') {
            /* Let's make sure we have the repository cloned to our workspace */
            checkout scm
        }
        stage('Example') {
            steps {
                echo "Choice: ${params.CHOICE}"
                sh "echo Choice: ${params.CHOICE}"
                sh 'echo Choice: $CHOICE'
            }
        }
    }
}
