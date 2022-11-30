---
title: Azure Kubernetes Service (AKS) Deployments Overview
description: A summary of Harness AKS implementation.
# sidebar_position: 2
helpdocs_topic_id: brwfq82umt
helpdocs_category_id: vbcmo6ltg7
helpdocs_is_private: false
helpdocs_is_published: true
---

This content is for Harness [FirstGen](/article/1fjmm4by22). Switch to [NextGen](/article/m7nkbph0ac).This topic describes the concept of a Harness Azure Kubernetes Service (AKS) deployment by describing the high-level steps involved.

For a vendor-agnostic, Harness Kubernetes deployment, see our [Kubernetes Deployments Overview](/article/wnr5n847b1-kubernetes-overview) doc.For a quick tutorial, see the [Kubernetes Quickstart](/article/7in9z2boh6-kubernetes-quickstart).

For detailed instructions on using AKS in Harness, see the [Azure How-tos](/category/gk062j3isk-azure-deployments).

This guide covers new the **Version 2** features of Harness' Kubernetes implementation for AKS. For Version 1 Kubernetes see [Harness Kubernetes v1 FAQ](/article/dtu3ud1ok7-kubernetes-and-harness-faq). For Helm deployment features, see [Helm Quickstart](/article/2aaevhygep-helm-quickstart).

### Before You Begin

Before learning about Harness Azure Kubernetes Service (AKS) deployments, you should have an understanding of [Harness Key Concepts](/article/4o7oqwih6h-harness-key-concepts).

### What Does Harness Need Before You Start?

A Harness AKS deployment requires the following:

1. Artifact: For example, a Docker image on Azure ACR.
2. Kubernetes cluster: You will need a target cluster for the Harness Delegate, your application, and your Kubernetes workloads. A Kubernetes Delegate requires at least 8GB RAM, and so your cluster should have enough RAM to host the Delegate and your applications and workloads.

### What Does Harness Deploy?

Harness takes the artifacts and Kubernetes manifests you provide and deploys them to the target AKS cluster. You can simply deploy Kubernetes objects via manifests and you can provide manifests using remote sources and Helm charts.



|  |  |
| --- | --- |
| Azure deployment in Harness Manager | The same deployment in Kubernetes Dashboard |
|  |  |

See [What Can I Deploy in Kubernetes?](/article/6ujb3c70fh).

### What Does a Harness AKS Deployment Involve?

The following list describes the major steps of a Harness AKS deployment:



|  |  |  |
| --- | --- | --- |
| **Step** | **Name** | **Description and Links** |
| 1 | Install the Harness Kubernetes **Delegate** in your AKS cluster.  | Typically, the Kubernetes Delegate is installed in the target AKS cluster where you will deploy your application(s). |
| 2 | Add a Harness **Artifact Server** or Harness **Azure Cloud Provider**. | The Harness **Artifact Server** is for artifact servers such as a Docker Registry Artifact Server. Harness connects to the Docker registry where your Docker images are located, or the public Docker Hub.If you want to obtain your artifacts from an ACR container, use an **Azure Cloud Provider**. |
| 3 | Add a **Kubernetes Cluster** **Cloud Provider**. | A Cloud Provider is a connection to your Kubernetes cluster.You can add a Kubernetes Cluster Cloud Provider (recommended) or a Cloud Provider for the cloud platform where the cluster is hosted, such as an Azure Cloud Provider. A Kubernetes Cluster Cloud Provider will connect to any cluster on any platform.In you use a Kubernetes Cluster Cloud Provider, you can use the Delegate installed in your cluster for authentication. |
| 4 | Create the Harness **Application** for your AKS CD Pipeline. | The Harness Application represents a group of microservices/containers, their deployment pipelines, and all the building blocks for those pipelines. Harness represents your release process using a logical group of one or more entities: Services, Environments, Workflows, Pipelines, Triggers, and Infrastructure Provisioners. Applications organize all of the entities and configurations in Harness CD. |
| 5 | Create the Harness **Service** using the **Kubernetes** Deployment Type. | Add your Kubernetes manifests and any config variables and files.You can use remote manifests stored in a source repo or Helm charts in a Helm repo. |
| 6 | Create the Harness **Environment** and Infrastructure Definition for your target AKS cluster, and any overrides. | Using the Harness Cloud Provider you set up, you can select the target AKS cluster and namespace for your deployment.You can also override any Service settings, such as manifest values. This enables you to use a single Service with multiple Harness Environments. |
| 7 | Create the Canary, Blue/Green, or Rollout deployment Harness **Workflow**. | The Workflow deploys the artifact(s) and Kubernetes workloads defined in the Harness Service to the cluster and namespace in the Harness Infrastructure Definition.See [Azure Workflows and Deployments](/article/x87732ti68-4-azure-workflows-and-deployments).For additional Workflows, see the vendor-agnostic steps in the following:* [Create a Kubernetes Canary Deployment](/article/2xp0oyubjj-create-a-kubernetes-canary-deployment)
* [Create a Kubernetes Blue/Green Deployment](/article/ukftzrngr1-create-a-kubernetes-blue-green-deployment)
* [Create a Kubernetes Rolling Deployment](/article/dl0l34ge8l-create-a-kubernetes-rolling-deployment)
 |
| 8 | Deploy the Workflow. | Once you've deployed a Workflow, learn how to improve your AKS CD:* [Workflows](/article/m220i1tnia-workflow-configuration)
* [Triggers](/article/xerirloz9a-add-a-trigger-2)
* [Infrastructure Provisioners Overview](/article/o22jx8amxb-add-an-infra-provisioner)
 |

### Next Steps

Read the following topics to build on what you've learned:

* [Azure (AKS) How-tos](/category/gk062j3isk-azure-deployments)
* [Kubernetes Quickstart](/article/7in9z2boh6-kubernetes-quickstart)
