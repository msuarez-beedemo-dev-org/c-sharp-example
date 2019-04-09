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
						def msbuildHome = tool name: 'default', type: 'hudson.plugins.msbuild.MsBuildInstallation'
						echo "msbuildHome=${msbuildHome}"
						bat "\"${msbuildHome}\\msbuild\" /t:Rebuild"
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
