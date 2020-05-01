node('linux') {

  stage('Prepare Workspace') {
    // clean
    deleteDir()

    checkout scm
  }


}

try {
  if (env.BRANCH_NAME == "sumt-master") {
      build job: 'Foundation Controls (Nightly)/' + "develop", wait: false
  }
} catch(e) {
  echo 'Unable to find the Foundation control branch for downstream building. Not failing the build for this...'
  emailext body: "Unable to find the Foundation control branch for bootsrap-additions repository in github. Please view the build information here: ${env.BUILD_URL}",
      from: 'Jenkins CI Server <jenkins-no-reply@sumtotalsystems.com>',
      subject: 'The foundation-controls project build has failed',
	  to: 'SumTotal-DevOps-Build@skillsoft.com'
	  
      throw err
}

