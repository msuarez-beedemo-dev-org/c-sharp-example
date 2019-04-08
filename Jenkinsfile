pipeline {
	agent {label 'Windows-agent'}
			stages{
				stage('Build'){
				  steps{
						 bat "MSBuild.SonarQube.Runner.exe begin /key:TestApp /name:ProjectName /version:1.0 /d:sonar.host.url=http://35.222.144.159:9000 /d:sonar.login=8d4766728abea4af633dc0caaf82f77888817c66"
					}
				}
				stage('Sonar Finish'){
					// finish
					// step([$class: 'MsBuildSQRunnerEnd'])
 				steps{
					bat "\"MSBuild.SonarQube.Runner.exe\" end"
				}
			}
			}
}
