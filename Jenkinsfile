pipeline {

  agent any

  stages {

    stage('Azure login'){

      steps{

        echo 'Entering Azure Session' 

        bat 'az login -u XXX -p XXX'

      }

    }

    stage('List Resource Groups'){

      steps{

        echo 'Getting Resource Groups' 

        bat 'az resource list'

      }

    }

    stage('Enable Azure Service Provider'){

      steps{

        bat 'az provider register -n Microsoft.Network'

        bat 'az provider register -n Microsoft.Storage'

        bat 'az provider register -n Microsoft.Compute'

        bat 'az provider register -n Microsoft.ContainerService'

      }

    }

    stage('Create Resource Group'){

      steps{

        bat 'az group create --name myResourceGroup1 --location eastus'

      }

    }

    stage('Create AKS Cluster'){

      steps{

        bat 'az aks create --resource-group myResourceGroup1 --name myAKSCluster1 --node-count 1 --node-vm-size Standard_D1_v2 --generate-ssh-keys'

      }

    }

  }

  post{

    always{

      echo 'Check your Azure mobile application'

    }

  }

}
