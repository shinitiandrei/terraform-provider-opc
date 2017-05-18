Terraform Provider for Oracle Compute Cloud
===========================================

- Website: https://www.terraform.io
- [![Gitter chat](https://badges.gitter.im/hashicorp-terraform/Lobby.png)](https://gitter.im/hashicorp-terraform/Lobby)
- Mailing list: [Google Groups](http://groups.google.com/group/terraform-tool)

![Terraform](https://rawgithub.com/hashicorp/terraform/master/website/source/assets/images/logo-hashicorp.svg)

Requirements
------------

-	[Terraform](https://www.terraform.io/downloads.html) 0.9.x
-	[Oracle Compute Cloud](https://cloud.oracle.com/compute) Account
-	[Go](https://golang.org/doc/install) 1.8 (to build the provider plugin)

Building The Provider
---------------------

Clone repository to: `$GOPATH/src/github.com/hashicorp/terraform-provider-opc`

```sh
$ mkdir -p $GOPATH/src/github.com/hashicorp; cd $GOPATH/src/github.com/hashicorp
$ git clone git@github.com:hashicorp/terraform-provider-opc
```

Enter the provider directory and build the provider

```sh
$ cd $GOPATH/src/github.com/hashicorp/terraform-provider-opc
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

Developing the OPC Provider
---------------------------

If you wish to work on the OPC provider, you'll first need [Go](http://www.golang.org) installed on your machine (version 1.8+ is *required*). You'll also need to correctly setup a [GOPATH](http://golang.org/doc/code.html#GOPATH), as well as adding `$GOPATH/bin` to your `$PATH`.

To compile the provider, run `make build`. This will build the provider and put the provider binary in the `$GOPATH/bin` directory.

```sh
$ make bin
...
$ $GOPATH/bin/terraform-provider-opc
...
```

In order to test the provider, you can simply run `make test`.

```sh
$ make test
```

In order to run the full suite of Acceptance tests, run `make testacc`.

*Note:* Acceptance tests create real resources, and often cost money to run.

```sh
$ make testacc
```

Using the environment variable `TESTARGS` we can limit the Acceptance tests that are ran to a specific test.
For example to solely run the basic SSH key acceptance test (`TestAccOPCSSHKey_basic`):

```sh
$ make testacc TESTARGS="-run=TestAccOPCSSHKey_basic"
```
