pipeline
{
    agent { node { label 'JDK11' } }
    triggers { pollSCM('* * * * *') }
    stages {
        stage('git') {
            steps {
                sh 'git checkout feature',
                sh 'git merge develop'
            }
        }
        stage('vcs') {
            steps {
                git url: 'https://github.com/satishnamgadda/shopizer_scripts.git',
                    branch: "feature"
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
