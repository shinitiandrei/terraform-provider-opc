Terraform Provider for Oracle Compute Cloud
===========================================

Requirements
------------

-	[Terraform](https://www.terraform.io/downloads.html) 0.8.x
-	[Oracle Compute Cloud](https://cloud.oracle.com/compute) Account
-	[Go](https://golang.org/doc/install) 1.7 (to build the provider plugin)

Building The Provider
---------------------

Clone repository to: `$GOPATH/src/github.com/oracle/terraform-provider-compute`

```sh
$ mkdir -p $GOPATH/src/github.com/hashicorp; cd $GOPATH/src/github.com/hashicorp
$ git clone git@github.com:hashicorp/terraform-provider-opc
```

Enter the provider directory and build the provider

```sh
$ cd provider
$ make build
```



Using the OPC provider
----------------------

Make sure that your `~/.terraformrc` file is written correctly for the `opc` provider:
```
# ~/.terraformrc

providers {
    opc = $GOPATH/bin/terraform-provider-opc
}
```

To authenticate with the Oracle Compute Cloud the provider will prompt for the required environment credentials. These credentails can be set in the following environment variables:

-	`OPC_ENDPOINT` - Endpoint provided by Oracle Public Cloud (e.g. https://api-z13.compute.em2.oraclecloud.com/\)
-	`OPC_USERNAME` - Username for Oracle Public Cloud
-	`OPC_PASSWORD` - Password for Oracle Public Cloud
-	`OPC_IDENTITY_DOMAIN` - Identity domain for Oracle Public Cloud

or directly in the terraform configuration:

```
provider "opc" {
  user = "xxxx@xxx"
  password = "xxxx"
  identityDomain = "xxxx"
  endpoint = "https://api-z13.compute.em2.oraclecloud.com/"
}
```

### Example Terraform configuration

An example [`test.tf`](test/test.tf) is provided that demonstatates the basic usage of the Oracle Compute Cloud Terraform Provider.

```sh
$ cd $GOPATH/src/github.com/hashicorp/terraform-provider-compute/test
$ terraform plan
$ terraform apply
$ terraform destroy
```
