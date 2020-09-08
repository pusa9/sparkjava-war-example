pipeline{
	agent any
	stages{
	
		stage('SCM - Checkout'){
			steps{
				git 'https://github.com/pusa9/spring-petclinic.git'
			
			}
		}
		stage('Maven Build'){
					steps{
					
						sh "mvn clean package"
					}
				
				}
			
                stage('Upload to nexus'){
					steps{
					
						nexusArtifactUploader artifacts: [[artifactId: 'myweb', classifier: '', file: 'target/my-app-0.0.7.war', type: 'war']], 
							credentialsId: 'nexus3',
							groupId: 'in.javahome', 
							nexusUrl: '172.31.2.179:8081', 
							nexusVersion: 'nexus3',
							protocol: 'http', 
							repository: 'venkat', 
							version: '0.0.7'
					}
				
				}
			}
