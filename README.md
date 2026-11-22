# Kubernetes-MongoDB-WebApp

<img src="https://githubusercontent.com" width="100" hspace="120" alt="Kubernetes Logo" />

The foundational architecture, demo application image, and project walkthrough for the manifests in this repository were inspired by [TechWorld with Nana](https://youtube.com) as part of a Kubernetes hands-on learning project.

The YAML configurations, local Minikube setup, and debugging implementations were written and configured entirely by me.

| File Name | Description |
| :--- | :--- |
| <code>mongo&#x2011;secret.yaml</code> | <details><summary><b>Expand</b></summary><br>**Description:**<br>A Kubernetes `Secret` manifest that securely stores Base64-encoded MongoDB root credentials (`mongo-user` and `mongo-password`). These values are injected as environment variables into both the database and web application pods.</details> |
| <code>mongo&#x2011;config.yaml</code> | <details><summary><b>Expand</b></summary><br>**Description:**<br>A Kubernetes `ConfigMap` manifest that holds non-sensitive configuration data, specifically the internal cluster DNS service name (`mongo-service`) used by the web application to locate the database.</details> |
| <code>mongo.yaml</code> | <details><summary><b>Expand</b></summary><br>**Description:**<br>Defines a `Deployment` running a MongoDB 5.0 container configured with root authentication from `mongo-secret`, paired with an internal `ClusterIP` `Service` (`mongo-service`) exposing port `27017` within the cluster.</details> |
| <code>webapp.yaml</code> | <details><summary><b>Expand</b></summary><br>**Description:**<br>Defines a `Deployment` for the Node.js user profile web application (`k8s-demo-app`) wired to both `mongo-secret` and `mongo-config`, paired with a `NodePort` `Service` (`webapp-service`) exposing port `3000` externally on `nodePort` `30100`.</details> |
