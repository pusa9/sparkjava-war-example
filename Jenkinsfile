pipeline{
	agent any
	stages{
	
		stage('SCM - Checkout'){
			steps{
				git 'https://github.com/pusa9/sparkjava-war-example.git'
			
			}
		}
		stage('Maven Build'){
					steps{
					
						sh "mvn clean package"
					}
				
				}
			
                stage('Upload to nexus'){
					steps{
					
						nexusArtifactUploader artifacts: [[artifactId: 'sparkjava-hello-world', classifier: '', file: 'target/sparkjava-hello-world-1.0.war', type: 'war']], 
							credentialsId: 'nexus3',
							groupId: 'sparkjava-hello-world', 
							nexusUrl: '172.31.2.179:8081', 
							nexusVersion: 'nexus3',
							protocol: 'http', 
							repository: 'venkat', 
							version: '1.0'
					}
				
				}
			}
