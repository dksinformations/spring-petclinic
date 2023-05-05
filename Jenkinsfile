pipeline{
    agent {'JDK_17'}
    stages {
        stage('VCS') {
            steps {
                git url: 'https://github.com/dksinformations/spring-petclinic.git'
                    branch: 'main'
            }
        }
        stage('package') {
            tools {
                jdk 'JDK_17'
            }
            steps {
                sh 'mvn package'
            }
        }
        stage('post build')
            steps {
                archiveArtifacts artifacts: '**/target/spring-petclinic-3.0.0-SNAPSHOT.jar'
                                 onlyIfSuccessful: true
                junit testresults: '**/surefire-reports/TEST-*.xml'
            }
    }
}
