def label = "worker-${UUID.randomUUID().toString()}"

podTemplate(label: label, containers: [
  containerTemplate(name: 'kubectl', image: 'lachlanevenson/k8s-kubectl:v1.8.8', command: 'cat', ttyEnabled: true)
],
) {
  node(label) {
    stage('Run kubectl') {
      container('kubectl') {
        sh "kubectl get pods --all-namespaces && kubectl apply -f deployment.yaml"
      }
    }
  }
}