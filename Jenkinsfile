pipeline {

  environment {
    dockerimagename = "bbilkevych/ruby-on-rails"
    dockerImage = ""
  }

  agent any

  stages {

    stage('Checkout Source') {
      steps {
        git 'https://github.com/Boniker/ruby-on-rails-deploy-kubernetes/tree/feature/add-ci'
      }
    }

    stage('Deploying App to Kubernetes') {
      steps {
        script {
          kubernetesDeploy(configs: "k8s/deploymentservice.yml", kubeconfigId: "KUBECONFIG_RANCHER")
        }
      }
    }
  }
}