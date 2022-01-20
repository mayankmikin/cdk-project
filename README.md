cdk-project (https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
## Hey guys this is my transition from a java devloper to a cloud developer using IAAS 

### install cdk (as a global package i.e. -g)
> sudo npm i -g aws-cdk
> cdk --version

## Refer this link https://cdkworkshop.com/20-typescript.html

## initialize a project in a non empty folder for me its cdkapp
> cdk init app --language typescript

* lib/cdk-workshop-stack.ts is where your CDK application’s main stack is defined. This is the file we’ll be spending most of our time in.
* bin/cdk-workshop.ts is the entrypoint of the CDK application. It will load the stack defined in lib/cdk-workshop-stack.ts.
package.json is your npm module manifest. It includes information like the name of your app, version, dependencies and build scripts like “watch” and “build” (package-lock.json is maintained by npm)
* cdk.json tells the toolkit how to run your app. In our case it will be "npx ts-node bin/cdk-workshop.ts"
tsconfig.json your project’s typescript configuration
* .gitignore and .npmignore tell git and npm which files to include/exclude from source control and when publishing this module to the package manager.
* node_modules is maintained by npm and includes all your project’s dependencies.

### will create a cloud formation template in cdk.out (ignored by git) and will be read by the aws for deployment and other stuff . check XXXtemplate.json

> cdk synth

### bootstrap the project (done only once when the project is created)

> cdk bootstrap
or 
> cdk bootstrap --profile devmum

this will deploy the stack with cdk toolkit
> cdk deploy


open cdk.json and you will see
"app": "npx ts-node --prefer-ts-exts bin/cdkapp.ts",   (starting point of our application)
npx = is a program that comes with a latest version of node and helps to download libraries
ts-node= so npx will download this library . this means we done thave to compile our program into javascript ourself ts node will do it for us
--prefer-ts-exts = means we will only use files with .ts extension
and will be executed by our 'bin/cdkapp.ts' file

### to check what are the difference in deployed app and what we have executed locally
> cdk diff

### show all environement configuration
> cdk doctor






















## ERRORS
Unable to resolve AWS account to use. It must be either configured when you define your CDK Stack, or through the environment

> nano ~/.aws/credentials
 
 now add this to your profile by getting values from IAM 
``` 
[devmum]
aws_access_key_id=''
aws_secret_access_key=''
aws_region=ap-south-1
```

> aws configure list-profiles
you will be able to see this