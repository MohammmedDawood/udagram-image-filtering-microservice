# Udagram Image Filtering Microservice

Udagram is a simple cloud application developed alongside the Udacity Cloud Engineering Nanodegree. It allows users to register and log into a web client, post photos to the feed, and process photos using an image filtering microservice.

## Table of Content

1. [Access Application](#access-application)
2. [Deployment - Getting Started](#deployment---getting-started)
   1. [Setup Application using AWS Elastic Beanstalk](#setup-application-using-aws-elastic-beanstalk)
3. [Local - Getting Started](#local---getting-started)
   1. [Setup Node Environment](#setup-node-environment)
4. [Resources](#resources)

## Access Application

AWS EB URL: http://image-filtering-dawood.eu-central-1.elasticbeanstalk.com/

Test API through this [link](http://localhost:8082/filteredimage?image_url=https://raw.githubusercontent.com/MohammmedDawood/deploy-a-static-website-on-aws/main/docs/images/website-homepage.png),
or check [Postman collection](/udagram-final.postman_collection.json).

![Udagram - Example](/deployment_screenshots/udagram_example.png)

**Note:**

> 20/01/2023: Website can be accessed through AWS with limited access.
> (Deployment status can be found [here](/deployment_screenshots/))

## Deployment - Getting Started

### Setup Application using AWS Elastic Beanstalk

1. Install AWS CLI v2
2. Run `aws configure`
3. Enter aws credentials
4. Run `eb init`
5. Enter Application Name `udagram-image-filtering-microservice`
6. Select runtime environment and platform `Node.js 14 running on 64bit Amazon Linux 2`

   ```shell
    Enter Application Name
    (default is "udagram-image-filtering-microservice"):
    Application udagram-image-filtering-microservice has been created.

    It appears you are using Node.js. Is this correct?
    (Y/n): y
    Select a platform branch.
    1) Node.js 16 running on 64bit Amazon Linux 2
    2) Node.js 14 running on 64bit Amazon Linux 2
    (default is 1): 1

    Do you wish to continue with CodeCommit? (Y/n): n
    Do you want to set up SSH for your instances?
    (Y/n): n
   ```

7. Add the below line in `config.yml` file
   ```shell
   deploy:
     artifact: ./www/Archive.zip
   ```
8. Run `npm run build`
9. Run `eb create`
10. Continue with default options

    ```shell
    Enter Environment Name
    (default is udagram-image-filtering-microservice-dev): image-filtering-dawood
    Enter DNS CNAME prefix
    (default is image-filtering-dawood):

    Select a load balancer type
    1) classic
    2) application
    3) network
    (default is 2): 2


    Would you like to enable Spot Fleet requests for this environment? (y/N): n
    Uploading udagram-image-filtering-microservice/app-b543-230120_103110764559.zip to S3. This may take a while.
    Upload Complete.
    Environment details for: image-filtering-dawood
      Application name: udagram-image-filtering-microservice
      Region: eu-central-1
      Deployed Version: app-b543-230120_103110764559
      Environment ID: e-j2tghnggma
      Platform: arn:aws:elasticbeanstalk:eu-central-1::platform/Node.js 16 running on 64bit Amazon Linux 2/5.6.3
      Tier: WebServer-Standard-1.0
      CNAME: image-filtering-dawood.eu-central-1.elasticbeanstalk.com
      Updated: 2023-01-20 08:31:13.377000+00:00
    Printing Status:
    2023-01-20 08:31:12    INFO    createEnvironment is starting.
    2023-01-20 08:31:14    INFO    Using elasticbeanstalk-eu-central-1-092571104767 as Amazon S3 storage bucket for environment data.
    2023-01-20 08:31:39    INFO    Created target group named: arn:aws:elasticloadbalancing:eu-central-1:092571104767:targetgroup/awseb-AWSEB-SEUU9UL6ZSAY/824e611436694996
    2023-01-20 08:31:39    INFO    Created security group named: sg-0ba0d081d6c148a4f
    2023-01-20 08:31:55    INFO    Created security group named: awseb-e-j2tghnggma-stack-AWSEBSecurityGroup-ERYU43R28Q62
    2023-01-20 08:31:55    INFO    Created Auto Scaling launch configuration named: awseb-e-j2tghnggma-stack-AWSEBAutoScalingLaunchConfiguration-e7W1QiPwwKJq
    2023-01-20 08:33:12    INFO    Created Auto Scaling group named: awseb-e-j2tghnggma-stack-AWSEBAutoScalingGroup-1CFT3IO2K405H
    2023-01-20 08:33:12    INFO    Waiting for EC2 instances to launch. This may take a few minutes.
    2023-01-20 08:33:28    INFO    Created Auto Scaling group policy named: arn:aws:autoscaling:eu-central-1:092571104767:scalingPolicy:62f7e211-3ffc-4662-ac4c-d7382555fe95:autoScalingGroupName/awseb-e-j2tghnggma-stack-AWSEBAutoScalingGroup-1CFT3IO2K405H:policyName/awseb-e-j2tghnggma-stack-AWSEBAutoScalingScaleDownPolicy-lJGcrlm16tVi
    2023-01-20 08:33:28    INFO    Created Auto Scaling group policy named: arn:aws:autoscaling:eu-central-1:092571104767:scalingPolicy:7ba9dd3d-5743-4caf-910b-ad7c15a0de8d:autoScalingGroupName/awseb-e-j2tghnggma-stack-AWSEBAutoScalingGroup-1CFT3IO2K405H:policyName/awseb-e-j2tghnggma-stack-AWSEBAutoScalingScaleUpPolicy-04dv8LsHtl1o
    2023-01-20 08:33:28    INFO    Created CloudWatch alarm named: awseb-e-j2tghnggma-stack-AWSEBCloudwatchAlarmLow-1GRK6G523P1C7
    2023-01-20 08:33:28    INFO    Created CloudWatch alarm named: awseb-e-j2tghnggma-stack-AWSEBCloudwatchAlarmHigh-EX5BY9FCOBVX
    2023-01-20 08:34:14    INFO    Created load balancer named: arn:aws:elasticloadbalancing:eu-central-1:092571104767:loadbalancer/app/awseb-AWSEB-105D359O1US4V/679b97c1e2cb95c4
    2023-01-20 08:34:14    INFO    Created Load Balancer listener named: arn:aws:elasticloadbalancing:eu-central-1:092571104767:listener/app/awseb-AWSEB-105D359O1US4V/679b97c1e2cb95c4/c1aefdd687c8ed60
    2023-01-20 08:34:24    INFO    Instance deployment: You didn't specify a Node.js version in the 'package.json' file in your source bundle. The deployment didn't install a specific Node.js version.
    2023-01-20 08:34:42    INFO    Instance deployment completed successfully.
    2023-01-20 08:35:16    INFO    Application available at image-filtering-dawood.eu-central-1.elasticbeanstalk.com.
    2023-01-20 08:35:16    INFO    Successfully launched environment: image-filtering-dawood
    ```

11. Go to Amazon Elastic Beanstalk
12. Check "Environments" page
    ![EB - Environments](/deployment_screenshots/eb_environments.png)
13. Check "Application" page
    ![EB - Applications](/deployment_screenshots/eb_applications.png)
14. Run `eb open`
    ![EB - Open](/deployment_screenshots/eb_open.png)
15. (Optional) If the code is modified after deployment, you can run `eb deploy`

```shell
Uploading udagram-image-filtering-microservice/app-81c0-230120_105908596453.zip to S3. This may take a while.
Upload Complete.
2023-01-20 08:59:09    INFO    Environment update is starting.
2023-01-20 08:59:13    INFO    Deploying new version to instance(s).
2023-01-20 08:59:16    INFO    Instance deployment: You didn't specify a Node.js version in the 'package.json' file in your source bundle. The deployment didn't install a specific Node.js version.
2023-01-20 08:59:34    INFO    Instance deployment completed successfully.
2023-01-20 08:59:40    INFO    New application version was deployed to running EC2 instances.
2023-01-20 08:59:40    INFO    Environment update completed successfully.

```

16. (Optional) If you want to remove all resources created and terminate, you can run `eb terminate image-filtering-dawood`

## Local - Getting Started

### Setup Node Environment

You'll need to create a new node server. Open a new terminal within the project directory and run:

1. Initialize a new project: `npm i`
2. run the development server with `npm run dev`

## Resources

- [How to deploy a Node.js app to the AWS Elastic Beanstalk](https://www.freecodecamp.org/news/how-to-deploy-a-node-js-app-to-the-aws-elastic-beanstalk-f150899ed977/)
