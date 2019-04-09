pipeline {
	environment{
		 MSBuild = 'C:\\Program Files (x86)\\Microsoft Visual Studio\\2019\\BuildTools\\MSBuild\\Current\\Bin\\MSBuild.exe'
	}
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
						bat ""${env.MSBuild} /t:Rebuild"
					}

				}

				stage('Sonar Finish'){
					// finish
					// step([$class: 'MsBuildSQRunnerEnd'])
 				steps{
				withSonarQubeEnv('Sonar') {
					bat "MSBuild.SonarQube.Runner.exe end"
				}
				}
			}
			}
}
