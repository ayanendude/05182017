node('master') {

stage ('Start'){}

    stage('DEV') {
        sh "echo Build"
		sh "pwd"
		sh "touch abc"
		parallel (
        "TRS Build": { 
		//build 'jenkins_build'
		stage ('Test'){ echo "TEST"}
		//test stage
            sh "echo TRS Build"
			sh "sleep 3"
        },
        "TMADMIN Build": { 
            sh "echo TMADMIN Build"
			sh "sleep 2"
        },
      )
    }
    stage('DEV Deploy'){
      parallel (
        "TRS Deploy": { 
            sh "echo TRS Deploy"
			sh "sleep 2"
        },
        "TMADMIN Deploy": { 
            sh "echo TMADMIN Deploy"
			sh "sleep 5"
        },
      )
    }
    stage('DEV Tests'){
      parallel (
        "TRS DEV Test": { 
            sh "echo TRS DEV Test"
			sh "sleep 2"
        },
        "TMADMIN DEV Test": { 
            sh "echo TMADMIN DEV Test"
			sh "sleep 5"
        },
      )
    }
	
	//checkpoint

	
	stage ('Pause') {
	input 'Proceed to UAT'
	def userInput = input(
 id: 'userInput', message: 'Let\'s promote?', parameters: [
 [$class: 'TextParameterDefinition', defaultValue: 'uat', description: 'Environment', name: 'env'],
 [$class: 'TextParameterDefinition', defaultValue: 'uat1', description: 'Target', name: 'target']
])
echo ("Env: "+userInput['env'])
echo ("Target: "+userInput['target'])

sh "echo env"
	}
	
	stage('UAT Deploy'){
	  parallel (
		"TRS Deploy": { 
			sh "echo TRS Deploy"
			sh "sleep 2"
		},
		"TMADMIN Deploy": { 
			sh "echo TMADMIN Deploy"
			sh "sleep 5"
		},
	  )
	}
    stage('UAT Tests'){
      parallel (
        "TRS Test": { 
            sh "echo TRS Test"
			sh "sleep 2"
        },
        "TMADMIN Test": { 
            sh "echo TMADMIN Test"
			sh "sleep 5"
        },
      )
    }
	
	stage ('ITSM ') {
	retry (2){
	input 'Proceed to PROD'
	}
	}
	
	
}