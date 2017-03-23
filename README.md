

# virtual-security-module

## Overview
VSM (Virtual Security Module) helps organizations to keep secrets (e.g. credentials) secure and manage their lifecycle.

Following is a list of high-level capabilities:
 * **Secure Storage of Secrets** - Each secret is encrypted using a generated encryption key which is not persisted anywhere. Instead,
   the encryption key is broken into pieces and each piece is kept in a different location potentially owned by a different person.
   An attacker has to penetrate into enough locations in order to reconstruct an encryption key. Furthermore, the attacker would
   have to break into enough locations simultaneously due to continuous share rotation.
 * **Multi-tenancy & Authorization** - Different secrets can reside in different namespaces, where each namespace might be owned and/or
   accessible by different organizations or users. Namespaces are hierarchical for easy management and quick revocation.
   Authorization is controlled through policies.
 * **Secret Lifecycle Management** - A secret is either handed off to the system to be kept securely, or is generated by the system
   (and kept securely) based on a client request. A secret can be read and used, updated if needed, auto-rotate in some cases and
   eventually destroyed – either automatically due to expiration or revoked based on a client request.
 * **Auditing** - Access and configuration modifications are audited. The auditing engine is pluggable through an audit adapter. The
   Level of audit is controlled through policies.
 * **Auto-rotating secrets** - A secret can be created dynamically based on a client request. An example is a short-lived AWS access
   token, that is automatically being refreshed periodically. This relieves the client from generating and refreshing such a secret
   while maximizing security through short-lived tokens and centralized auditing. Multiple types of secrets, like certificates and
   cloud access keys, are supported.
 * **AuthN** - Pluggable authentication is supported through an abstraction of an identity provider and support for multiple
   authentication protocols.
 * **Client-side library** - a library to help protect the authentication credentials required to connect to the VSM server itself is
   provided.
 * **High-Availability & Scale-Out** - the server can be configured as a cluster for high-availability and scale-out.
 * **RESTful API and documentation** - the server's API is RESTful and its documentation is generated and browsable through integration
   with Swagger.
 * **Command-line client tool** - for easy interaction with the server

## Try it out

### Prerequisites

* To run: none
* To build: Golang 1.7+ (https://golang.org/doc/install)
* To generate RESTful API docs: go-swagger (https://github.com/go-swagger/go-swagger)

### Build, Test & Run

1. Under your Go workspace create a **src/github.com/vmware** directory.
```
mkdir -p src/github.com/vmware
```
2. cd into **src/github.com/vmware** and clone your forked repo.
```
git clone https://github.com/$yourusername/virtual-security-module
```
3. cd into **virtual-security-module**
```
cd virtual-security-module
```
4. Before your first build fetch dependencies by running:
```
make install-deps
```
5. To build run:
```
make
```
6. To test run:
```
make test
```
7. To generate RESTful API docs run:
```
make doc
```
8. To start the server run:
```
./dist/vsmd
```
9. To start the cli tool run:
```
./dist/vsm-cli
```

## Documentation
The [HOWTO](doc/HOWTO.md) describes how to accomplish some common tasks.

## Releases & Major Branches

## Contributing

The virtual-security-module project team welcomes contributions from the community. If you wish to contribute code and you have not
signed our contributor license agreement (CLA), our bot will update the issue when you open a Pull Request. For any
questions about the CLA process, please refer to our [FAQ](https://cla.vmware.com/faq). For more detailed information,
refer to [CONTRIBUTING.md](CONTRIBUTING.md).

## License
