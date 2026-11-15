
node {
    def mvnHome = tool 'MAVEN_HOME'

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
}
