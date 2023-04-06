# Deploy your Plugin to the Cloud

After [creating your custom plugin](./), you need to ensure the Python script associated with it is running at all times, otherwise users will not be able to run the plugin.

This is why it is usually preferable, for production-level plugins, to deploy your code to a third-party computing service instead of running it locally on your machine.

This page will detail one of the many ways in which you can deploy your code to a remote computing service. We will containerize our plugin, then we will use [AWS LightSail](https://aws.amazon.com/lightsail/), a service which  allows us to deploy Docker containers to the cloud.

## Prerequisites

* Have Docker installed on your local machine. ([Guide](https://docs.docker.com/get-docker/))
* Have AWS-CLI installed on your local machine. ([Guide](https://lightsail.aws.amazon.com/ls/docs/en\_us/articles/amazon-lightsail-install-software))
* Have a AWS account and have IAM credentials created on AWS. ([Guide](https://lightsail.aws.amazon.com/ls/docs/en\_us/articles/amazon-lightsail-managing-access-for-an-iam-user))
* Have your AWS CLI configured. ([Guide](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html))

## Deployment Steps

### 1. Create a LightSail Container Service

1. Sign in to the [LightSail console](https://lightsail.aws.amazon.com/).
2. Enter the [containers](https://lightsail.aws.amazon.com/ls/webapp/home/containers) tab.
3. Choose [_Create Container Service_](https://lightsail.aws.amazon.com/ls/webapp/create/container-service)
4. Choose _Change AWS Region_, then pick the region from which you'd like to run your plugin.
5. Choose a capacity for your container service.

### 2. Build your Plugin as a Docker Image

From your terminal, navigate to your plugin's folder, and run

```
docker build -t
```

### 3. Upload your Docker Image to Lightsail

From your terminal, navigate to the folder containing your newly-created Docker image, and run

```
aws lightsail push-container-image --region <Region> --service-name <ContainerServiceName> --label <ContainerImageLabel> --image <LocalContainerImageName>:<ImageTag>
```

More information on this command can be found [here in the LightSail documentation](https://lightsail.aws.amazon.com/ls/docs/en\_us/articles/amazon-lightsail-pushing-container-images).

### 4. Deploy your Image

From the LightSail dashboard, go to the _Containers_ tab and select your container. Then,

1. Choose _Create a deployment_
2. You can specify here custom deployment options. Pick your Docker image to create a deployment.
3. The deployment form will open. From here, you'll be able to input deployment parameters such as environmental variables. [More detail on deployment parameters on LightSail here](https://lightsail.aws.amazon.com/ls/docs/en\_us/articles/amazon-lightsail-container-services-deployments#creating-container-deployments-parameters).
4. Choose _Save and deploy_ to deploy your Docker image on the container service. Your plugin will be up and running on LightSail.
