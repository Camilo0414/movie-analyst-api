// This shows a simple example of how to archive the build output artifacts.
node {
    stage("clean"){
    cleanWs()
    }

    stage("checkout"){
        git branch: 'master', url: 'https://github.com/Camilo0414/movie-analyst-api.git'
    }

    //INSTALATION PREVIOUSLY MADE
    // stage("install"){
    //     sh 'curl -sL https://deb.nodesource.com/setup_10.x | bash -'
    //     sh 'apt-get install -y nodejs'
    // }

    stage("build"){
        sh 'export PORT=3000'
        sh 'npm install'
    }

    stage("test"){
        sh 'npm run test'
    }

    stage("deploy"){
        sh 'ssh -i /var/jenkins_home/.ssh/id_rsa ec2-user@10.0.3.26 rm -rf /home/ec2-user/backend'
        sh 'ssh -i /var/jenkins_home/.ssh/id_rsa ec2-user@10.0.2.107 rm -rf /home/ec2-user/backend'
        
        sh 'scp -rp -i /var/jenkins_home/.ssh/id_rsa /var/jenkins_home/workspace/rampup/backend ec2-user@10.0.3.26:/home/ec2-user/backend'
        sh 'scp -rp -i /var/jenkins_home/.ssh/id_rsa /var/jenkins_home/workspace/rampup/backend ec2-user@10.0.2.107:/home/ec2-user/backend'
    }
}
