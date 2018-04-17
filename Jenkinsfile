node("docker") {
    docker.withRegistry('https://hub.docker.com/r/rockabhi58/demo_devops/', 'mydockerhub') {
    
        git url: "https://github.com/birajdarabhishek1/dockerpipeline.git", credentialsId: 'mygithub'
    
        sh "git rev-parse HEAD > .git/commit-id"
        def commit_id = readFile('.git/commit-id').trim()
        println commit_id
    
        stage "build"
        def app = docker.build "docker"
    
        stage "publish"
        app.push 'master'
        app.push "${commit_id}"
    }
}
