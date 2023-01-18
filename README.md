# Azure Machine Learning CLI V2 In a Day Workshop

The aim of this workshop is to help customers to install and test AML CLI V2. The total time for this workshop is around 1 to 2 hours.

### Lab 1 - Install and set up the CLI (v2) - Time: 10 to 20 min

Read this tutorial and follow the instructions:<BR> 
https://docs.microsoft.com/en-us/azure/machine-learning/how-to-configure-cli<BR>

```
az extension list
az extension remove -n azure-cli-ml
az extension remove -n ml
az extension add -n ml -y
az ml -h
az extension update -n ml
az login
```

### Lab 2 - Run Azure Machine Learning CLI V2 Hello World - Time: 10 to 20 min

Read this tutorial and follow the instructions:<BR>
https://docs.microsoft.com/en-us/azure/machine-learning/how-to-train-cli <BR>

Clone the Repo:
```
git clone --depth 1 https://github.com/Azure/azureml-examples
cd azureml-examples/cli
```

Create a resource group and location of resource
```
az group create -n cliv2demo -l uksouth
```

Create a machine learning workspace:
```
az ml workspace create -n cliv2amldemo -g cliv2demo -l uksouth
```

Create compute
```
az ml compute create -n cpu-cluster --type amlcompute --min-instances 0 --max-instances 8 --resource-group cliv2demo --workspace-name cliv2amldemo
az ml compute create -n gpu-cluster --type amlcompute --min-instances 0 --max-instances 4 --size Standard_NC12 --resource-group cliv2demo --workspace-name cliv2amldemo
```

Run Hello world.yml
```
az ml job create -f jobs/basics/hello-world.yml --web --resource-group cliv2demo --workspace-name cliv2amldemo
```

### Lab 3 - Run end to end NYC example and CIFAR-10 example - Time: 10 to 30 min

Run NYC Taxi example 
```
az ml job create -f jobs/pipelines/nyc-taxi/pipeline.yml --web --resource-group cliv2demo --workspace-name cliv2amldemo
```

Run CIFAR-10 example 
```
az ml job create -f jobs/pipelines/cifar-10/pipeline.yml --web --resource-group cliv2demo --workspace-name cliv2amldemo
```

  
### Lab 4 - Run a R Script - Time: 10 min

Run Iris R example 
```
az ml job create -f jobs/single-step/r/iris/job.yml --web --resource-group cliv2demo --workspace-name cliv2amldemo
```
  
Run Accidents R example 
```
az ml job create -f jobs/single-step/r/accidents/job.yml --web --resource-group cliv2demo --workspace-name cliv2amldemo
```  

  
### Learn more
https://www.youtube.com/watch?v=unbzStG3IVY&t=3s <BR>
https://github.com/Azure/azureml-examples <BR>
https://caiomsouza.medium.com/azure-machine-learning-cli-2-0-v2-84fef15e7b9 <BR>
https://techcommunity.microsoft.com/t5/azure-ai-blog/announcing-the-new-cli-and-arm-rest-apis-for-azure-machine/ba-p/2393447 <BR>

  
