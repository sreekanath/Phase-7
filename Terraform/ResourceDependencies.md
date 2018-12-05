### Resource Dependencies

* Assigning an Elastic IP:

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

* Apply Changes: terraform apply

        Terraform is creating two resources
        
        + aws_eip.ip
        + aws_instance.example
        
          aws_instance.example: Creating...
          ami:                          "" => "ami-0ac019f4fcb7cb7e6"
          arn:                          "" => "<computed>"
          associate_public_ip_address:  "" => "<computed>"
          availability_zone:            "" => "us-east-1b"
          cpu_core_count:               "" => "<computed>"
          cpu_threads_per_core:         "" => "<computed>"
          ebs_block_device.#:           "" => "<computed>"
          ephemeral_block_device.#:     "" => "<computed>"
          get_password_data:            "" => "false"
          instance_state:               "" => "<computed>"
          instance_type:                "" => "t2.micro"
          ipv6_address_count:           "" => "<computed>"
          ipv6_addresses.#:             "" => "<computed>"
          key_name:                     "" => "<computed>"
          network_interface.#:          "" => "<computed>"
          network_interface_id:         "" => "<computed>"
          password_data:                "" => "<computed>"
          placement_group:              "" => "<computed>"
          primary_network_interface_id: "" => "<computed>"
          private_dns:                  "" => "<computed>"
          private_ip:                   "" => "<computed>"
          public_dns:                   "" => "<computed>"
          public_ip:                    "" => "<computed>"
          root_block_device.#:          "" => "<computed>"
          security_groups.#:            "" => "<computed>"
          source_dest_check:            "" => "true"
          subnet_id:                    "" => "<computed>"
          tenancy:                      "" => "<computed>"
          volume_tags.%:                "" => "<computed>"
          vpc_security_group_ids.#:     "" => "<computed>"
        aws_instance.example: Still creating... (10s elapsed)
        aws_instance.example: Still creating... (20s elapsed)
        aws_instance.example: Still creating... (30s elapsed)
        aws_instance.example: Creation complete after 32s (ID: i-0a12f688f07e532b0)
        aws_eip.ip: Creating...
          allocation_id:     "" => "<computed>"
          association_id:    "" => "<computed>"
          domain:            "" => "<computed>"
          instance:          "" => "i-0a12f688f07e532b0"
          network_interface: "" => "<computed>"
          private_ip:        "" => "<computed>"
          public_ip:         "" => "<computed>"
          public_ipv4_pool:  "" => "<computed>"
          vpc:               "" => "<computed>"
        aws_eip.ip: Creation complete after 0s (ID: eipalloc-01b100419491dcbbe)

        Apply complete! Resources: 2 added, 0 changed, 0 destroyed.
