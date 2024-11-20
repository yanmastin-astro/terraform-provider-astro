## Developer Requirements

- [Terraform](https://developer.hashicorp.com/terraform/downloads) >= 1.7
- [Go](https://golang.org/doc/install) >= 1.21

## Building The Provider

1. Clone the repository
2. Enter the repository directory
3. Build the provider using the following `Makefile` command:

```shell
make dep
make build
```

4. The provider binary will be available in the `bin` directory

## Adding Dependencies

This provider uses [Go modules](https://github.com/golang/go/wiki/Modules).
Please see the Go documentation for the most up-to-date information about using Go modules.

To add a new dependency `github.com/author/dependency` to your Terraform provider:

```shell
go get github.com/author/dependency
go mod tidy
```

Then commit the changes to `go.mod` and `go.sum`.

## Developing the Provider

If you wish to work on the provider, you'll first need [Go](http://www.golang.org) installed on your machine (see [Requirements](#developer-requirements) above).

To compile the provider, see [Building The Provider](#building-the-provider).

To add example docs, add the correspond `.tf` files to the `examples` directory. These should be added for every new data source and resource.

To run terraform with the provider, create a `.terraformrc` file in your home directory (`~`) with the following content to override the provider installation with the local build:

```hcl
provider_installation {
  dev_overrides {
    "registry.terraform.io/astronomer/astro" = "~/terraform-provider-astro/bin" # Your path to the provider binary
  }
  direct {}
}
```

## Contributing to the Provider's Development

Submit pull requests, report issues, or suggest improvements on the GitHub repository.
See [CONTRIBUTING.md](CONTRIBUTING.md) for more.
