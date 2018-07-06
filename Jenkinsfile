node() {
	
	stage('Checkout') {
		
		checkout scm
	}
	

	stage('Build') {
		
		def GRADLE_HOME = tool name: "gradle-4" , type: 'gradle'
		
		withEnv(["PATH+GRADLE=$GRADLE_HOME/bin"]) {
			bat "gradle compile"
		}
	}	

	stage('Test') {
		
		def GRADLE_HOME = tool name: "gradle-4" , type: 'gradle'
		
		withEnv(["PATH+GRADLE=$GRADLE_HOME/bin"]) {
			bat "gradle cucumber"
		}
		step([$class: 'JUnitResultArchiver', testResults: 'build/test-results/test/**/*.xml'])
	}	
	
	stage('Arifact publish') {
		
		archive 'build/libs/*.jar'
	}	
	
}