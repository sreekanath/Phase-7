Refer: 

* Intro: https://www.terraform.io/intro/index.html

* Install: https://learn.hashicorp.com/terraform/getting-started/install.html

* Setup the path: https://stackoverflow.com/questions/14637979/how-to-permanently-set-path-on-linux-unix

* Providers(Terraform can support these provides) : https://www.terraform.io/docs/providers/index.html

1. Download the terraform binary package.

        wget https://releases.hashicorp.com/terraform/0.11.10/terraform_0.11.10_linux_amd64.zip
        
2. unzip the package & path setup

        apt-get update -y && apt-get install unzip -y
        
        unzip terraform_0.11.10_linux_amd64.zip

        mv terraform /var/lib/terraform
        
        export PATH="$PATH:/var/lib/"
        
        terraform -version

3.  Examples: AWS

    3.1. Install awscli to configure the credentials.

        apt-get install awscli -y

    3.2. Create an user in IAM with "AmazonEC2FullAccess". 
    
        aws configure
        
        root@ip-172-31-47-245:~# aws configure
        AWS Access Key ID [None]: AKIAIE************FA
        AWS Secret Access Key [None]: mbC***************8wSfq3UytJ
        Default region name [None]: us-east-1
        Default output format [None]: json
        
    3.3. example.tf
    
        provider "aws" {
           region     = "us-east-1"
        }

        resource "aws_instance" "example" {
          ami           = "ami-0ac019f4fcb7cb7e6"
          instance_type = "t2.micro"
        }
        
     3.4. terraform init


         root@ip-172-31-47-245:~# terraform init

        Initializing provider plugins...
        - Checking for available provider plugins on https://releases.hashicorp.com...
        - Downloading plugin for provider "aws" (1.50.0)...

        The following providers do not have any version constraints in configuration,
        so the latest version was installed.

        To prevent automatic upgrades to new major versions that may contain breaking
        changes, it is recommended to add version = "..." constraints to the
        corresponding provider blocks in configuration, with the constraint strings
        suggested below.

        * provider.aws: version = "~> 1.50"

        Terraform has been successfully initialized!

        You may now begin working with Terraform. Try running "terraform plan" to see
        any changes that are required for your infrastructure. All Terraform commands
        should now work.

        If you ever set or change modules or backend configuration for Terraform,
        rerun this command to reinitialize your working directory. If you forget, other
        commands will detect it and remind you to do so if necessary.

    3.5. terraform apply
    
        root@ip-172-31-87-186:~# terraform apply

                An execution plan has been generated and is shown below.
                Resource actions are indicated with the following symbols:
                  + create

                Terraform will perform the following actions:

                  + aws_instance.example
                      id:                           <computed>
                      ami:                          "ami-0ac019f4fcb7cb7e6"
                      arn:                          <computed>
                      associate_public_ip_address:  <computed>
                      availability_zone:            <computed>
                      cpu_core_count:               <computed>
                      cpu_threads_per_core:         <computed>
                      ebs_block_device.#:           <computed>
                      ephemeral_block_device.#:     <computed>
                      get_password_data:            "false"
                      instance_state:               <computed>
                      instance_type:                "t2.micro"
                      ipv6_address_count:           <computed>
                      ipv6_addresses.#:             <computed>
                      key_name:                     <computed>
                      network_interface.#:          <computed>
                      network_interface_id:         <computed>
                      password_data:                <computed>
                      placement_group:              <computed>
                      primary_network_interface_id: <computed>
                      private_dns:                  <computed>
                      private_ip:                   <computed>
                      public_dns:                   <computed>
                      public_ip:                    <computed>
                      root_block_device.#:          <computed>
                      security_groups.#:            <computed>
                      source_dest_check:            "true"
                      subnet_id:                    <computed>
                      tenancy:                      <computed>
                      volume_tags.%:                <computed>
                      vpc_security_group_ids.#:     <computed>

                Plan: 1 to add, 0 to change, 0 to destroy.

                Do you want to perform these actions?
                  Terraform will perform the actions described above.
                  Only 'yes' will be accepted to approve.

                  Enter a value: yes

                aws_instance.example: Creating...
                  ami:                          "" => "ami-0ac019f4fcb7cb7e6"
                  arn:                          "" => "<computed>"
                  associate_public_ip_address:  "" => "<computed>"
                  availability_zone:            "" => "<computed>"
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
                aws_instance.example: Creation complete after 21s (ID: i-01f5cacffc16e33b7)

                Apply complete! Resources: 1 added, 0 changed, 0 destroyed.
                root@ip-172-31-87-186:~#



