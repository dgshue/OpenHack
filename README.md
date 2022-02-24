# OpenHack Deployment Files

This directory contains the source code and Kubernetes manifests for the OpenHack TripViewer Application. This example code is based on the guestbook tutorial from Kubernetes.

Follow the tutorial at https://kubernetes.io/docs/tutorials/stateless-application/guestbook/ for ways to adapt the current example code to fit our challenges.


# Useful Links

https://docs.microsoft.com/en-us/azure/aks/cluster-container-registry-integration?tabs=azure-cli

# Secrets

| Secret Name   |    Key        |    Description    |
| ------------- | --------      | ----------------  |
| openhack      | SQL_USER      | SQL User Account  |
| openhack      | SQL_PASSWORD  | SQL Password      |
| openhack      | SQL_SERVER    | SQL Server FQD    |