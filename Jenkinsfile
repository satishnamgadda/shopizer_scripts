pipeline
{
    agent { node { label 'JDK11' } }
    triggers { cron('30 5 * * *') }
    stages {
        stage('vcs') {
            steps {
                git url: 'https://github.com/satishnamgadda/shopizer.git',
                    branch: "release"
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
