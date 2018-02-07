@Library('tivoPipeline') _

emailBreaks {
    node('docker') {
        stage('Code Checkout'){
            git 'https://github.com/TiVo/docker-alpine-java.git'
        }
        stage('Build Docker Images') {
            dir('8/162b12/server-jre/standard/') {
                docker.withRegistry('https://docker.tivo.com', 'docker-registry') {
                    def image = docker.build("alpine-java:8_server-jre", "--pull .")
                    image.push()
                }
            }
            dir('8/162b12/jdk/standard/') {
                docker.withRegistry('https://docker.tivo.com', 'docker-registry') {
                    def image = docker.build("alpine-java:8_jdk", "--pull .")
                    image.push()
                }
            }
        }
    }
}
