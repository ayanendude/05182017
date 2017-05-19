node('master') {

stage ('Start'){}

    stage('DEV Build') {
        sh "echo Build"
		      parallel (
        "TRS Build": { 
            sh "echo TRS Build"
			sh "sleep 2"
        },
        "TMADMIN Build": { 
            sh "echo TMADMIN Build"
			sh "sleep 12"
        },
      )
    }
    stage('DEV Deploy'){
      parallel (
        "TRS Deploy": { 
            sh "echo TRS Deploy"
			sh "sleep 12"
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
	
	stage ('Pause') {
	input 'Proceed to UAT'
	}
	
	stage('UAT Deploy'){
	  parallel (
		"TRS Deploy": { 
			sh "echo TRS Deploy"
			sh "sleep 12"
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
	input 'Proceed to PROD'
	}
	
	
}