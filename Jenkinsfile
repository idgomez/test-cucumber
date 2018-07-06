node() {
	
	stage('Checkout') {
		
		checkout scm
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