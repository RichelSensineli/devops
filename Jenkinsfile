node {
    def app

    stage('Clonar repositorio') {
         
        checkout scm
    }

    stage('Buildar imagem do docker') {

        app = docker.build("edsonrjunior/devops_g1_ex5")
    }

    stage('Push da imagem para o Dockerhub') {

        docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
            app.push("latest")
        }
    }

    stage('Deploy do container via ansible-playbook') {

        sh '/usr/bin/ansible-playbook playbook.yml'
        
        sh 'whoami'
    }
}