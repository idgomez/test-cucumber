node() {
	
	stage('Checkout') {
		
		checkout scm
	}
	

	stage('Build') {
		
		def GRADLE_HOME = tool name: "gradle-4" , type: 'gradle'
		
		withEnv(["PATH+GRADLE=$GRADLE_HOME/bin"]) {
			bat "gradle build -x test"
		}
	}	

	stage('Test') {
		
		def GRADLE_HOME = tool name: "gradle-4" , type: 'gradle'
		
		withEnv(["PATH+GRADLE=$GRADLE_HOME/bin"]) {
			bat "gradle build cucumber"
		}
		step([$class: 'JUnitResultArchiver', testResults: 'build/test-results/test/**/*.xml'])
	}	
	
	stage('Arifact publish') {
		
		archiveArtifacts 'build/libs/*.jar'
	}	
	
}