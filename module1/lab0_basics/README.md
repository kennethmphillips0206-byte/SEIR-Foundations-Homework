# SEIR Foundations — Module 1, Lab 0

## Deployment Evidence

| Deployment | Instance ID | Public IPv4 Address | Dashboard Verified | Terminated |
|---|---|---|---|---|
| 1 | `i-009cbac524152f14e` | `3.90.188.127` | Yes | Yes |
| 2 | `i-09a0302a782ef33c8` | `100.54.193.43` | Yes | Yes |
| 3 | `i-064598b5e315acbf8` | `54.221.17.7` | Yes | Yes |

## Deployment 1

I launched an EC2 instance from my saved launch template, connected using EC2 Instance Connect, and verified that the SEIR dashboard appeared. I recorded the public IPv4 address and saved the dashboard screenshot.

## Deployment 2

I repeated the launch and connection process with a second instance. The SEIR dashboard displayed successfully, and I recorded a different public IPv4 address and saved the screenshot.

## Deployment 3

I completed a third deployment using the saved launch template. I connected using EC2 Instance Connect, verified the dashboard, and recorded a third distinct public IPv4 address.

## Understanding the Dashboard

- **CPU:** Shows the approximate processing activity of the instance.
- **Memory:** Shows RAM usage compared with total available memory.
- **Disk:** Shows how much storage is used compared with the total capacity.
- **Uptime:** Shows how long the instance has been running.

## What Became Easier

After repeating the process, I became more comfortable finding my launch template, launching EC2 instances, connecting through EC2 Instance Connect.

## An Issue I ran into and fixed

I accidentally launched an extra practice instance while working through the steps. I identified it in the EC2 Instances page and terminated it.

## Cleanup and Launch Template

I retained my `seir-lab0-template` launch template and terminated the practice instances after completing the deployments.
