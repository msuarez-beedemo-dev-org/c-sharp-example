pipeline {

	agent {label 'Windows-agent'}
			stages{
				stage('Start Scanning'){
				  steps{
						withSonarQubeEnv('Sonar') {
						 bat "MSBuild.SonarQube.Runner.exe begin /key:TestApp /name:CSharpApp /version:1.0"
					 }
					}

				}
				stage('Build'){
					steps{
							bat "\"${tool 'MSBuild'}\""
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
