pipeline {
    agent {
        label ''
    }
    environment {
        image = "puwadol/nodejs"
        registry = "docker.io"
    }
    stages {
        // stage('Ansible prepareations docker ') {
        //     steps{
        //         sh 'ANSIBLE_ROLES_PATH="$PWD/ansible-script/roles" ansible-playbook -vvv ./ansible-script/playbook/web-server/web-server.yml -i ./ansible-script/host -u root -e "state=prepareation tagnumber=${BUILD_NUMBER}"'
        //     }
        // }
        
        stage('Build docker image') {
            steps {
                script {
                   sh "docker build -f ./Dockerfile -t ${env.image} ."
                }
            }
        }

        stage('Deployment'){
            steps {
                sh "docker-compose up -d"
            }
            
        }

        // stage('tag docker image') {
        //     steps {
        //        sh "docker tag ${env.image}:${BUILD_NUMBER} ${env.image}:latest"
        //     }
        // }

        // stage('push docker image') {
        //     steps {
        //        sh "docker push ${env.image}:latest"
        //     }
        // }

        // stage('Verify new docker image(s)') {
        //     steps {
        //         sh('docker images')
        //     }
        // }
        
    }
}

