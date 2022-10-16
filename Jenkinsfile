pipeline
{
    agent { node { label 'JDK11' } }
    stages {
        stage('vcs') {
            steps {
                git url: 'https://github.com/satishnamgadda/shopizer.git',
                    branch: "master"
            }  
        }
        stage('build') {
            steps {
                sh '/usr/share/maven/bin/mvn package'
            }
        }
        stage('artifacts') {
            steps {
            archiveArtifacts artifacts: 'sm-core/target/*.jar', followSymlinks: false
            }
        }
        stage('results') {
            steps {
            junit 'sm-shop/target/surefire-reports/*.xml'
            }
        }
    }
}
