pipeline {
	agent {label 'Windows-agent'}
			stages{
				stage('Start Scanning'){
				  steps{
						withSonarQubeEnv('Sonar') {
						 bat "MSBuild.SonarQube.Runner.exe begin /key:TestApp /name:ProjectName /version:1.0"
					 }
					}

				}
				stage('Build'){
					steps{
						bat 'MSBuild.exe /t:Rebuild'
					}

				}

				stage('Sonar Finish'){
					// finish
					// step([$class: 'MsBuildSQRunnerEnd'])
 				steps{
					bat "MSBuild.SonarQube.Runner.exe end"
				}
			}
			}
}
