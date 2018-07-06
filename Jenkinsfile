node() {
	
	stage('Checkout') {
		
		checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'github', url: 'https://github.com/idgomez/test-cucumber.git']]])
	}
	

	stage('Build') {
		
		def GRADLE_HOME = tool name: "gradle-4" , type: 'gradle'
		
		withEnv(["PATH+GRADLE=$GRADLE_HOME/bin"]) {
			bat "gradle build"
		}
	}	

	stage('Test') {
		
		def GRADLE_HOME = tool name: "gradle-4" , type: 'gradle'
		
		withEnv(["PATH+GRADLE=$GRADLE_HOME/bin"]) {
			bat "gradle cucumber"
		}
	}		
}