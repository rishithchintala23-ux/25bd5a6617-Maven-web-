
node {
    def mvnHome = tool 'MAVEN_HOME'

    try {
        stage('Checkout') {
            git branch: 'master',
                url: 'https://github.com/rishithchintala23-ux/25bd5a6617-Maven-web-.git'
        }

        stage('Build') {
            bat "\"${mvnHome}\\bin\\mvn.cmd\" clean package"
        }

        stage('Test') {
            bat "\"${mvnHome}\\bin\\mvn.cmd\" test"
        }

        stage('Archive') {
            archiveArtifacts artifacts: 'target/*.war'
        }

        emailext(
            to: 'YOUR_EMAIL@gmail.com',
            subject: "SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
            body: "Jenkins pipeline completed successfully. ${env.BUILD_URL}"
        )

    } catch (Exception e) {
        currentBuild.result = 'FAILURE'

        emailext(
            to: 'YOUR_EMAIL@gmail.com',
            subject: "FAILURE: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
            body: "Jenkins pipeline failed. Check: ${env.BUILD_URL}"
        )

        throw e
    }
}
