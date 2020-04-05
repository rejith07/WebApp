
node {
    // Get Artifactory server instance, defined in the Artifactory Plugin administration page.
    def server = Artifactory.server "artifactory"
    // Create an Artifactory Maven instance.
    def rtMaven = Artifactory.newMavenBuild()
    def buildInfo
    
 rtMaven.tool = "maven"

    stage('Clone sources') {
        git url: 'https://github.com/rejith07/webapp.git'
    }


    stage('Maven build') {
        buildInfo = rtMaven.run pom: 'pom.xml', goals: 'compile'
    }

    stage('Publish build info') {
        server.publishBuildInfo buildInfo
    }
    }
	 
