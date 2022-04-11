# postgrestest
Helm charts for testing connection to Postgres database

## Installation

You need [helm3](https://helm.sh/docs/intro/install/) to install this chart. 

To install this helm chart run the following command.

    helm install postgrestest .\postgres-test\

When installing this helm chart don't forget to set the configuration options mentioned below in the values.yaml file.

## Configuration

You can configure the installation by adjusting the values.yaml or by providing your own configuration. All values missing in your own configuration file will be used from the default values.yaml. 

### configuration options

The following options are available in the values.yaml:

environment_variables:
* host        : The endpoint of the Postgres database
* database    : The name of the database
* user        : The username of the user configured in the database
* password    : The password of the user

If configured correctly you should see the following message:

    Connecting to the PostgreSQL database...
    PostgreSQL database version:
    ('PostgreSQL version number, compiled by Visual C++ build 1914, 64-bit',)
    Database connection closed.

### Usage

To see the response from the pod you can do the following steps:

1. Get the pod name with the command: kubectl get pods
2. Get the pod logs with the command: kubectl logs <pod-name>


### Troubleshooting

The connect() function raises the DatabaseError exception if an error occurred.

For example, if your host is not accessible, the program will output the following message:

    Connecting to the PostgreSQL database...
    could not translate host name "localhosts" to address: Unknown host
    Code language: Shell Session (shell)

The following displays error message when you change the database to a database that does not exist e.g., supplier:

    Connecting to the PostgreSQL database...
    FATAL: database "supplier" does not exist
    Code language: Shell Session (shell)

If you change the user to a user that does not exist, it will not be authenticated successfully as follows:

    Connecting to the PostgreSQL database...
    FATAL: password authentication failed for user ""
