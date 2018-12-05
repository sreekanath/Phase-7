### Input Variables

 cat variables.tf
 
    variable "region" {
      default = "us-east-1"
    }
    variable "instance_ami" {
      default = "ami-0ac019f4fcb7cb7e6"
    }
    variable "instance_type" {}
    
 cat example.tf
 
    provider "aws" {
       region     = "${var.region}"
    }

    resource "aws_instance" "example" {
      ami           = "${var.instance_ami}"
      instance_type = "${var.instance_type}"
    }
    
 Command-line flags: terraform apply -var 'instance_type=t2.micro' 


   
