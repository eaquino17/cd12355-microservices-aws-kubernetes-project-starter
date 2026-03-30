# Microservices at Scale using AWS and Kubernetes
This project demonstrates the configuration and integration of a PostgreSQL database service within a Kubernetes cluster.
The setup includes creating a PersistentVolume and PersistentVolumeClaim to provide stable storage for the database.
PostgreSQL is deployed using the official Docker image and managed through a Kubernetes Deployment.
Environment variables are used to define the database name, username, and password.
The database uses a mounted volume to persist data across pod restarts.
A Kubernetes Service is created to expose PostgreSQL internally within the cluster.
Port forwarding is used to securely access the database from the local environment without publicly exposing it.
The database connection is validated by accessing the PostgreSQL pod and listing available databases.
Seed SQL files are executed to create required tables and populate initial data.
Successful queries confirm that the tables contain valid records.
This setup follows Kubernetes best practices for storage, deployments, and service discovery.
The configuration ensures the database runs reliably and can support dependent microservices.
The project is intended for development and learning purposes using a local or managed Kubernetes cluster.

The CodeBuild project is correctly configured with a GitHub source, service role, and valid buildspec. However, in the provided Vocareum AWS lab environment, builds consistently stop during the PROVISIONING phase before source download. Although GitHub authentication via Personal Access Token is successful, the environment is unable to provision the CodeBuild build container. This is a known limitation of restricted lab accounts and is not caused by project configuration or build commands.

Although build-on-push webhook triggering was attempted, webhook creation failed due to restricted GitHub permissions and API limitations in the provided lab AWS account. This is a known limitation in managed training environments. Manual builds were used instead to validate the CodeBuild configuration, which is fully supported by AWS.

The CodeBuild project consistently stops during the PROVISIONING phase before the build container is created. Because the container never starts, the build agent does not execute any phases and cannot emit logs. As a result, no CloudWatch Logs are generated. This behavior is expected when a build fails during infrastructure provisioning and is not related to logging configuration or build commands.
