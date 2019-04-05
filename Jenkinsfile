pipeline {
	agent {label 'Windows-agent'}
			stages{
				stage('Build'){
				  steps{
						 bat "MSBuild.SonarQube.Runner.exe\" begin /key:ProjectKey /name:ProjectName /version:1.0"
					}
				}
				stage('Sonar Finish'){
					// finish
					// step([$class: 'MsBuildSQRunnerEnd'])
					bat "\"${sonarHome}\\MSBuild.SonarQube.Runner.exe\" end"
				}
				
			}
}
