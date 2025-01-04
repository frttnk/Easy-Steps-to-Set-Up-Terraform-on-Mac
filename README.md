

 <h1 align="center">Easy Steps to Set Up Terraform on Mac</h1>

<br/>
<p align="center">
 Step-by-Step Guide to Installing and Configuring Terraform for AWS Infrastructure
</p>
<br/>

<p align="center">
   <img src="https://github.com/user-attachments/assets/4ccccc2a-d168-4324-810e-4c0c3a110c46" />
</p>

<br/>

This guide will teach you about Terraform and how to install it on macOS. You can start using Terraform once you are done with all the steps.

<br/>

> This guide is created to reference future guides, focusing on the installation and setup.

<br/>

### What is Terraform?

Terraform is an infrastructure as code (IaC) tool that allows you to manage your resources through code. With Terraform, you can create and modify your infrastructure easily and efficiently.

Terraform provides:

1. An infrastructure-as-code approach that helps you create, modify, and delete your resources through code.

2. Automation of resource creation, modification, and destruction, which reduces direct human interaction with resources and minimizes the risk of human error.

3. Support for multiple cloud providers.

4. The ability to collaborate with your team by sharing Terraform files.

5. State management features that allow you to make and revert changes to your resources easily.

6. The capability to handle complex and large infrastructures.

### Installing Terraform

Installing Terraform is a straightforward process that requires you to visit their [website](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli).

<br/>

<p align="center">
   <img src="https://github.com/user-attachments/assets/124e4fcc-49f2-4daf-94c3-d1f29135284a" />
</p>

<br/>

Follow the steps based on your operating system.

<br/>

<p align="center">
   <img src="https://github.com/user-attachments/assets/acae798a-1d02-4022-9c24-7f2e13f8b1bc" />
</p>

<br/>

Since I use macOS, I selected `Homebrew on macOS`. Open a terminal and execute the command `brew tap hashicorp/tap`.

<br/>

<p align="center">
   <img src="https://github.com/user-attachments/assets/c9343641-3d2f-4457-b4b6-f9f404f01b02" />
</p>

<br/>

Then execute the command `brew install hashicorp/tap/terraform`.

<br/>

<p align="center">
   <img src="https://github.com/user-attachments/assets/bccf9b80-1455-4771-aedb-30847d25b718" />
</p>

<br/>

After the installation is complete, run the command `brew update`, and then finally, execute `brew upgrade hashicorp/tap/terraform`.

<br/>

<p align="center">
   <img src="https://github.com/user-attachments/assets/021ca750-476b-44e0-837e-b199a287f56f" />
</p>

<br/>

### Testing Terraform

After following all the steps, we should test Terraform to verify it's working correctly. To do this, execute the command `terraform -help`. You should see the following output if Terraform is installed on your machine.

<br/>

<p align="center">
   <img src="https://github.com/user-attachments/assets/1bb19c43-60e6-419f-94cc-2f670efdc157" />
</p>

<br/>

### Configuring AWS for Terraform

We need to make sure that `aws cli` is installed on our computer before we start managing AWS resources. Let's install the `aws cli` by executing the command `brew install awscli`. You should see a similar output at the end of the process.

<br/>

<p align="center">
   <img src="https://github.com/user-attachments/assets/7de61da0-dbeb-4acd-963c-c03a3c6fc8a1" />
</p>

<br/>

Then, let's verify the installation by executing the command `aws --version`.

<br/>

<p align="center">
   <img src="https://github.com/user-attachments/assets/bc0cc99b-2a24-4674-a775-afb6830f46a2" />
</p>

<br/>

Since we can see the version of the `aws cli`, we can run aws configure to configure AWS credentials. First, go to the AWS Management Console and create an `Access Key` and `Secret Access Key`. Search for `IAM` and select the first result.

<br/>

<p align="center">
   <img src="https://github.com/user-attachments/assets/796cfbde-119d-4002-8178-8c2b0f7dfa32" />
</p>

<br/>

Click on `Users` and then click on `Create User`

<br/>

<p align="center">
   <img src="https://github.com/user-attachments/assets/ed116640-3acf-48de-8393-8d74b4b4bd06" />
</p>

<br/>

Enter a `User name` then click on `Next`

<br/>

<p align="center">
   <img src="https://github.com/user-attachments/assets/38a3fb34-afdc-44be-bec8-f97c433e988f" />
</p>

<br/>

On the Set Permissions page, select `Attach policies directly` and search for `AdministratorAccess`. Assign it to the user, as we will need admin access to test our Terraform configuration. Then click on `Next`.

<br/>

<p align="center">
   <img src="https://github.com/user-attachments/assets/4e721d86-e784-4e4a-8ff0-50ea7703d560" />
</p>

<br/>

Review all the details and click on `Create User` if everything looks good.

<br/>

<p align="center">
   <img src="https://github.com/user-attachments/assets/18a7e40e-5934-414b-981d-eca3f25d767f" />
</p>

<br/>

If the process is successful, you should see the user in the list.


<br/>

<p align="center">
   <img src="https://github.com/user-attachments/assets/8282f30a-9f56-4d6e-815f-b432716b7deb" />
</p>

<br/>

Now, we need to create an `Access Key`. To do this, click on the `User Name`, select `Security Credentials`, and then click on `Create Access Key`.

<br/>

<p align="center">
   <img src="https://github.com/user-attachments/assets/a4c3bc1d-cead-40a4-a42b-e5ee2c1c968b" />
</p>

<br/>

On the next page, select `Command Line Interface (CLI)` because we want to use the `AWS CLI`. Check the `Confirmation` box, then click on `Next`.

<br/>

<p align="center">
   <img src="https://github.com/user-attachments/assets/1c722cc5-728c-4ad2-8dd5-7965bb671f9c" />
</p>

<br/>

You can enter a description if you want, as it is optional, and then click on `Create Access Key`.


<br/>

<p align="center">
   <img src="https://github.com/user-attachments/assets/530905d9-79b8-4035-a8dd-7c37d0efd035" />
</p>

<br/>

On the next page, you will see your `Access Key` and `Secret Access Key`. You must save these details because you will not see `Secret Access Key` again after clicking on `Done`. You can either download them or save them to a notepad. 

<br/>

<p align="center">
   <img src="https://github.com/user-attachments/assets/7c66d6d2-1721-400b-ba1d-49c68f2211c9" />
</p>

<br/>

Now, go back to the terminal and create a folder by executing the command `mkdir <folder_name>`. Navigate to the folder you just created and run `code .` to open it in VS Code.

<br/>

<p align="center">
   <img src="https://github.com/user-attachments/assets/5ae0b83e-a988-4f07-8d02-ff0766672aff" />
</p>

<br/>

Open a Terminal and execute the command `aws configure`, then enter your AWS credentials.

<br/>

<p align="center">
   <img src="https://github.com/user-attachments/assets/915eaf17-dd91-487b-8b7d-122d664c0522" />
</p>

<br/>

Let's go to `Extensions` in VS Code and install the `HashiCorp Terraform` extension.

<br/>

<p align="center">
   <img src="https://github.com/user-attachments/assets/30ee1bb4-c7e6-4e86-9263-708d12df760d" />
</p>

<br/>


### Testing Terraform Configuration

Now, we can create a Terraform file and test our configuration to verify it's working. Create a file named `main.tf` and copy the following configuration code.

<br/>

```
data "aws_ami" "linux"{
    most_recent = true

    filter{
        name = "name"
        values = ["amzn2-ami-hvm-*-x86_64-gp2"]
    }

    filter{
        name = "owner-id"
        values = ["137112412989"] # Amazon's official AMI owner ID
    }
}

resource "aws_instance" "ecommerce_server" {
  ami           = data.aws_ami.linux.id
  instance_type = "t2.micro"

    tags = {
    Name = "Terraform Test"
  }
}
```

<br/>

Next, we need to execute these commands in sequence:

1. `terraform init` to initialize the configuration requirements

2. `terraform plan` to preview what will be created

3. `terraform apply -auto-approve` to create the EC2 instances

> The `-auto-approve` flag allows us to skip the approval step after executing `terraform apply`. Without this flag, you would need to type `yes` when Terraform asks for approval.

Go to the AWS Management Console and check the EC2 instance list to verify the deployment.


<br/>

<p align="center">
   <img src="https://github.com/user-attachments/assets/d09828b7-ed8f-44c3-adf4-cfdf5e563b2a" />
</p>

<br/>

If you can see `Terraform Test` in the instance list, it means our configuration is working, and we can use Terraform from now on to create our infrastructure on AWS.

<br/>

<p align="center">
   <img src="https://github.com/user-attachments/assets/8758528f-7445-4174-b36f-ebbe0c32ecef" />
</p>

<br/>

We need to run the command `terraform destroy -auto-approve` to avoid additional costs.

In this guide, we covered how to install and configure Terraform on macOS to manage AWS infrastructure. As a result, following these simple steps will help you set up Terraform and start managing AWS resources.

For more articles, <a href="https://www.firattonak.com" target="_blank">visit FiratTonak.com</a>


