# Helm Chart Repository

This repository hosts Helm charts for Kubernetes applications.

## Prerequisites

- [Helm](https://helm.sh/docs/intro/install/) installed
- A GitHub repository to store your Helm charts
- A local clone of your repository:
  ```sh
  git clone https://github.com/JoePalmeras66/helm-repo.git
  cd helm-repo
  ```

## Creating a New Helm Chart

To create a new Helm chart, use the following command:

```sh
helm create <chart-name>
```

For example, to create a chart named `my-app`:

```sh
helm create my-app
```

This will generate a directory structure for your chart inside the repository.

## Adding the Chart to the Repository

Once you have created and customized your Helm chart, package it using:

```sh
helm package my-app
```

This will generate a `.tgz` file (e.g., `my-app-0.1.0.tgz`).

Next, update the `index.yaml` to include your new chart:

```sh
helm repo index . --url https://raw.githubusercontent.com/JoePalmeras66/helm-repo/main/
```

This updates the `index.yaml` file to reference your packaged chart.

## Pushing the Chart to GitHub

Commit and push the changes to your GitHub repository:

```sh
git add .
git commit -m "Added my-app Helm chart"
git push origin main
```

## Using the Helm Repository

To use the repository in your Kubernetes cluster:

1. Add the repository:
   ```sh
   helm repo add my-helm-repo https://raw.githubusercontent.com/JoePalmeras66/helm-repo/main/
   ```

2. Update the Helm repo:
   ```sh
   helm repo update
   ```

3. Install the chart:
   ```sh
   helm install my-release my-helm-repo/my-app
   ```

## Automating Updates with GitHub Actions (Optional)

To automate the process of packaging and indexing charts, you can set up a GitHub Action. Let me know if you need help with this!

## License

This repository is open source and available under the [MIT License](LICENSE).

