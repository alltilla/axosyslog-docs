---
title: Install AxoSyslog with Helm
linktitle: Helm
weight: 300
---

AxoSyslog provides [Helm charts for syslog-ng](https://github.com/axoflow/axosyslog-charts/). You can use these charts to install [cloud-ready syslog-ng images]({{< relref "/docs/_index.md#images" >}}) created and maintained by [Axoflow](https://axoflow.com).

## Prerequisites

You must have [Helm 3.0 or newer](https://helm.sh) installed to use these charts. Refer to the [official Helm documentation](https://helm.sh/docs/intro/install/) for details.

## Limitations

The chart provides parameters that make it easy to:

- collect logs using the [`kubernetes()`]({{< relref "/docs/configure-source/kubernetes/_index.md" >}}) source, and
- forward the logs using the `network()` and `opensearch()` destinations.

To use other sources and destinations, use the `config.raw` parameter. For the list of configurable parameters and their default values, see {{% xref "/docs/install/helm/helm-chart-parameters.md" %}}.

## Install

To install the `axosyslog-collector` charts, complete the following steps.

1. Clone the chart repository.

    ```bash
    git clone git@github.com:axoflow/axosyslog-charts.git
    cd axosyslog-charts
    ```

1. Install the chart. The following command installs `axosyslog-collector` into the `default` namespace. For the list of configurable parameters and their default values, see {{% xref "/docs/install/helm/helm-chart-parameters.md" %}}.

    ```bash
    helm install --generate-name charts/axosyslog-collector
    ```

    ```bash
    NAME: axosyslog-collector-1683469360
    LAST DEPLOYED: Sun May  7 16:22:40 2023
    NAMESPACE: default
    STATUS: deployed
    REVISION: 1
    TEST SUITE: None
    NOTES:
    1. Watch the axosyslog-collector-1683469360 container start.
      $ kubectl get pods --namespace=default -l app=axosyslog-collector-1683469360 -w
    ```

1. Check that the pod is running.

    ```bash
    kubectl get pods
    ```

    The output should look like:

    ```bash
    NAME                                   READY   STATUS    RESTARTS   AGE
    axosyslog-collector-1683469360-tptfb   1/1     Running   0          28s
    ```

## Uninstall

> **Tip**: List all installed releases using `helm list`.

To uninstall a chart release, run:

```bash
helm delete <name-of-the-release-to-delete>
```

## Contribute

If you have fixed a bug or would like to contribute your improvements to these charts, [open a pull request](https://github.com/axoflow/axosyslog-charts/pulls). We truly appreciate your help.
