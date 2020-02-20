# terraform-demo

This repo has an example of getting started with terraform.  

## Prerequisite:

I have already configured the [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-configure.html) 

## Deploying AWS EC2 instance using Terraform (.tf file)

`aws-example.tf`

Using AWS cloud platform for this example to create the EC2 instance (t2-macro as its a free tier)
```javascript
provider "aws" {
  profile    = "default"
  region     = "us-east-1"
}
````
Creating `t2.macro` instance using `ami` `ami-b374d5a5`
```javascript

resource "aws_instance" "example" {
  ami           = "ami-b374d5a5"
  instance_type = "t2.micro"
  // Below code will create the ip_address.txt file which will have a IP address of newly created instance
  provisioner "local-exec" {
    command = "echo ${aws_instance.example.public_ip} > ip_address.txt"
  }
}
````


