# Open Data Hub Custom Notebook Sizes

## Goal

Create a custom notebooks size in [Open Data Hub](https://opendatahub.io) (ODH)

## Steps

1. Install [ODH](https://opendatahub.io/docs/getting-started/quick-installation.html)
2. Navigate to the namespace where ODH is installed
3. Navigate to `ConfigMaps` in the navigation panel
4. Click the `Create ConfigMap` button
5. Paste the below sample `ConfigMap` over all default text and click `Create`. This will add a new notebook size to the Jupyter console named `XX-Large-Memory`

    ```yaml
    kind: ConfigMap
    apiVersion: v1
    metadata:
      name: developer-jupyterhub-sizes
      namespace: sepsis
      labels:
        jupyterhub: singleuser-profiles
    data:
      jupyterhub-singleuser-profiles.yaml: |
        sizes:
          - name: XX-Large-Memory
            resources:
              requests:
                memory: 1Gi
                cpu: 1
              limits:
                memory: 16Gi
                cpu: 4
    ```
