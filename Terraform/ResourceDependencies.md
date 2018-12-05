### Resource Dependencies

Assigning an Elastic IP:

        provider "aws" {
           region     = "us-east-1"
        }

        resource "aws_instance" "example" {
          ami           = "ami-0ac019f4fcb7cb7e6"
          instance_type = "t2.micro"
          availability_zone = "us-east-1b"
        }

        resource "aws_eip" "ip" {
          instance = "${aws_instance.example.id}"
        }
