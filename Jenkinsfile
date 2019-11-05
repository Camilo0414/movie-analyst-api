// This shows a simple example of how to archive the build output artifacts.
node {
    stage("clean"){
    cleanWs()
    }

    stage("checkout"){
        git branch: 'master', url: 'https://github.com/Camilo0414/movie-analyst-api.git'
    }

    stage("build"){
        sh 'export PORT=3000'
        sh 'npm install'
    }

    stage("test"){
        sh 'npm run test'
    }

    stage("deploy"){

        sh 'scp -rp -i /var/jenkins_home/.ssh/id_rsa /var/jenkins_home/workspace/rampup/backend/ ec2-user@10.0.3.119:/home/ec2-user/backend'
        sh 'ssh -i /var/jenkins_home/.ssh/id_rsa ec2-user@10.0.3.119 forever start /home/ec2-user/backend/server.js'

        sh 'scp -rp -i /var/jenkins_home/.ssh/id_rsa /var/jenkins_home/workspace/rampup/backend/ ec2-user@10.0.2.179:/home/ec2-user/backend'
        sh 'ssh -i /var/jenkins_home/.ssh/id_rsa ec2-user@10.0.2.179 forever start /home/ec2-user/backend/server.js'
    }
}
