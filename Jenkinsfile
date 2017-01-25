node("docker") {
    docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-codefish') {
    
        git url: "https://github.com/ahmedali-durga/sample-maven-project.git", credentialsId: 'github-ahmedali-durga'
    
        sh "git rev-parse HEAD > .git/commit-id"
        def commit_id = readFile('.git/commit-id').trim()
        println commit_id
    
        stage "build"
        def app = docker.build "sample-maven-project"
    
        stage "publish"
        app.push 'master'
        app.push "${commit_id}"
    }
}