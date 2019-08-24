podTemplate(
    containers: [containerTemplate(name: 'golang', image: 'golangr', ttyEnabled: true, command: 'cat')],
    //volumes: [hostPathVolume(hostPath: '/var/run/docker.sock', mountPath: '/var/run/docker.sock')]
    namespace: 'kube-jenkins',
    nodeSelector: "ip-172-26-14-103.ap-northeast-2.compute.internal"
          
)
{
node(POD_LABEL) {
        container('golang') {
             stage('Clone') {
                container('docker') {
                    checkout scm
                }
            }

            stage('Build') {
                container('helm') {
                    sh "go build"
                }
            }
        
        }
    }
}
