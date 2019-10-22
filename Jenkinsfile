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
        sh 'scp -rp -i /var/jenkins_home/.ssh/id_rsa /var/jenkins_home/workspace/rampup/backend/ ec2-user@10.0.4.5:/home/ec2-user/movie-analyst-api'
    }
}
