---
date: 2022-12-05
description: "Learn about the importance of preventing external changes to managed resources in a Terraform provider and
how this helps maintain the integrity of the infrastructure."
path: "the-importance-of-preventing-external-changes-to-managed-resources-in-a-terraform-provider"
published: true
tags: ['terraform', 'dev']
title: "The Importance of Preventing External Changes to Managed Resources in a Terraform Provider"
---

Hey again!

## Introduction

In order to understand why it is important for a Terraform provider not to allow external changes to the managed
resources, it's helpful to consider the role of Terraform in managing infrastructure.

Terraform is a popular IaaC tool that allows users to define and manage their infrastructure using configuration files.
These files specify the desired state of the infrastructure, including details such as the number and types of resources
to be created, and the settings and configurations for each resource.

When the Terraform configuration files are applied, the Terraform provider is responsible for creating and managing the
specified resources. This includes tasks such as provisioning new resources, updating existing resources, and deleting
resources that are no longer needed.

## The Importance

If changes to the managed resources are allowed from external sources, such as other IaaC tools or API clients, it can
lead to conflicts and inconsistencies in the infrastructure. For example, if a resource is updated through the Web UI
while Terraform is in the process of updating the same resource, the resulting state of the resource may be
unpredictable.

It is important for the Terraform provider to prevent external changes to the managed resources in order to maintain the
integrity of the infrastructure.

## Developing a Terraform Provider

By default, Terraform will check for external changes whenever it is applied and take appropriate action, such as
reverting the changes or prompting the user for confirmation before proceeding.

This default behavior helps to ensure that the infrastructure remains in a predictable and consistent state, and that
all changes to the managed resources are made through the Terraform configuration files. This can help to prevent
conflicts and ensure that your infrastructure is consistently managed and maintained.

When developing a Terraform provider, it is important to understand and adhere to this behavior in order to ensure that
the provider is able to effectively manage the infrastructure.
