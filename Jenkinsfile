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
							bat "\"${tool 'MSBuild'}\" /t:Rebuild"
					}

				}

				stage('Sonar Finish'){
 				steps{
				withSonarQubeEnv('Sonar') {
					bat "MSBuild.SonarQube.Runner.exe end"
					}
					}
				}
				stage('Nuget push'){
					steps{
								bat "nuget.exe pack Package.nuspec"
								withCredentials([string(credentialsId: 'Nuget Token', variable: 'token')]) {
									bat "nuget.exe push Package.1.0.0.nupkg ${token} -Source http://35.222.19.76:32000/repository/nuget.org-proxy/"
							}
					}
				}

			}
}
