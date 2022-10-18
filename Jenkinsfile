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
    } 
}
