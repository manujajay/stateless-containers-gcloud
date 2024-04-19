# Stateless Containers on Gcloud

This repository offers a comprehensive guide on deploying stateless containers using Google Cloud services such as Google Kubernetes Engine (GKE) and Cloud Run. It covers containerization basics, deployment, scaling, and best practices for managing stateless applications.

## Prerequisites

- Google Cloud account
- Basic knowledge of Docker and containerization
- Installed Google Cloud SDK

## Installation

### Setting Up Google Kubernetes Engine (GKE)

1. **Create a GKE cluster**:
   ```bash
   gcloud container clusters create "my-cluster" --zone "us-central1-a" --num-nodes "3"
   ```

2. **Deploy a stateless application**:
   - Create a Docker container and push it to Google Container Registry (GCR).
   - Deploy the container to GKE:
     ```bash
     kubectl create deployment my-app --image=gcr.io/YOUR_PROJECT_ID/my-app
     ```

### Using Google Cloud Run

1. **Deploy a container to Cloud Run**:
   - Ensure your container is stateless and listens on the HTTP port defined by the `PORT` environment variable.
   - Deploy using:
     ```bash
     gcloud run deploy --image gcr.io/YOUR_PROJECT_ID/my-app --platform managed
     ```

## Scaling and Management

- **GKE Autoscaling**:
  - Set up horizontal pod autoscaling based on CPU usage:
    ```bash
    kubectl autoscale deployment my-app --cpu-percent=50 --min=1 --max=10
    ```

- **Cloud Run Autoscaling**:
  - Automatically managed by the platform, scales down to zero when not in use.

## Best Practices

- Ensure your containers are stateless; manage state using external services like Cloud SQL or Cloud Memorystore.
- Use managed services like Cloud Run for ease of deployment and management.
- Monitor your applications using Google Cloud's operations suite.

## Contributing

Contributions to improve setup guides, add examples, or enhance best practices are welcome. Please fork the repository, make your changes, and submit a pull request.

## License

This project is licensed under the MIT License. See the LICENSE file for more details.
