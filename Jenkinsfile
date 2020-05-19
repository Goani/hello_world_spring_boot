def label = "worker-${UUID.randomUUID().toString()}"

podTemplate(label: label, containers: [
  containerTemplate(name: 'kubectl', image: 'lachlanevenson/k8s-kubectl:v1.18.2', command: 'cat', ttyEnabled: true)
],
) {
  node(label) {
    stage('Run kubectl') {
      container('kubectl') {
        checkout scm
        sh "kubectl apply -f deployment.yaml"
      }
    }
  }
}