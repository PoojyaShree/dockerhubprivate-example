node{
    def app
    stage('scm'){
        git branch: 'main', url: 'https://github.com/PoojyaShree/dockerhubprivate-example.git'
    }
    stage('build the image'){
        app=docker.build("gaddamnarendra/myprivaterepo",".")
    }
    stage('test image'){
        app.inside{
            sh 'echo "tested successfully"'
        }
    }
    stage('push image'){
        docker.withRegistry('https://registry.hub.docker.com','DOCKER_CRDS'){
            app.push("latest")
            app.push("${env.BUILD_NUMBER}")
        }
    }
}
