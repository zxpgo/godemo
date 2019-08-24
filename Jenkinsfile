podTemplate(
    containers: [containerTemplate(name: 'golang', image: 'golang', ttyEnabled: true, command: 'cat')],
    volumes: [hostPathVolume(hostPath: '/root/godata', mountPath: '/root/godata/')],
    namespace: 'kube-jenkins',
    nodeSelector: "ip-172-26-14-103.ap-northeast-2.compute.internal"
          
)
{
node(POD_LABEL) {
        container('golang') {
             stage('Clone') {

                    checkout scm

            }

            stage('Build') {
                    sh "go get -u github.com/gorilla/mux"
                    sh "go build -o hello-server"
                sh "pwd"
                sh "cp -r /home/jenkins/agent/workspace/  /root/godata"
            }
        
        }
    }
}
