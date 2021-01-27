# Deploying Dag/Ingress Template

[![Releases](https://img.shields.io/github/release/f5networks/f5-aws-cloudformation-v2.svg)](https://github.com/f5networks/f5-aws-cloudformation-v2/releases)
[![Issues](https://img.shields.io/github/issues/f5networks/f5-aws-cloudformation-v2.svg)](https://github.com/f5networks/f5-aws-cloudformation-v2/issues)




## Contents

- [Deploying Dag/Ingress Template](#deploying-dag-template)
  - [Contents](#contents)
  - [Introduction](#introduction)
  - [Prerequisites](#prerequisites)
  - [Important Configuration Notes](#important-configuration-notes)
  - [Resources Provisioning](#resources-provisioning)
    - [Template Input Parameters](#template-input-parameters)
    - [Template Outputs](#template-outputs)
  - [Resource Creation Flow Chart](#resource-creation-flow-chart)



## Introduction

This solution uses an AWS Cloud Formation template to launch a stack for provisioning Dag/Ingress related items. This template can be deployed as a standalone; however the main intention is to use as a module for provisioning Dag/Ingress related resources:


  
## Prerequisites

  - None. This template does not require provisioning of additional resources.
  
  
## Resources Provisioning

   - [External Load Balancer](https://docs.aws.amazon.com/elasticloadbalancing/latest/classic/elb-internet-facing-load-balancers.html)
   - [Internal Load Balancer](https://docs.aws.amazon.com/elasticloadbalancing/latest/classic/elb-internal-load-balancers.html)
   - Public IP Addresses
     * Management
     * External 

### Template Input Parameters

| Parameter | Required | Description |
| --- | --- | --- |
| application | No | Name of the Application Tag |
| costcenter | No | Name of the Cost Center Tag |
| environment | No | Name of the Environment Tag |
| externalSubnetAz1 | No | Availability Zone 1 External Subnet Id |
| externalSubnetAz2 | No | Availability Zone 2 External Subnet Id |
| group | No | Name of the Group Tag |
| internalSubnetAz1 | No | Availability Zone 1 Internal Subnet Id |
| internalSubnetAz2 | No | Availability Zone 2 Internal Subnet Id |
| numberPublicExternalIPAddresses | Yes | Min 0, Max 4 - Number of external public ip address to create |
| numberPublicMgmtIPAddresses | Yes | Min 0, Max 4 - Number of public management ip addresses to create |
| owner | No | Name of the Application Tag |
| provisionExternalBigipLoadBalancer | No | Flag to provision external Load Balancer |
| provisionInternalBigipLoadBalancer | No | Flag to provision internal Load Balancer |
| provisionPublicIP | No | Flag to provision Management and External Public IPs |
| restrictedSrcAddress | Yes | The IP address range used to SSH and access management GUI on the EC2 instances |
| restrictedSrcAddressApp | Yes | The IP address range that can be used to access web traffic (80/443) to the EC2 |
| restrictedSrcPort | Yes | The management port used for BIGIP management GUI |
| vpc | No | Provides VPC Id |


### Template Outputs

| Name | Description | Required Resource | Type |
| --- | --- | --- | --- |
| StackName | bigip-standalone nested stack name | bigip-standalone template deployment | String |
| BigipManagementEipAddress | BIGIP Management Public IP  | None | string |
| BigipExternalEipAddress | BIGIP External Public IP  | None | string |
| ExternalElasticLoadBalancer | External Load Balancer Id | None | string |
| InternalElasticLoadBalancer | Internal Load Balancer Id  | None | string |
| InternalTargetGroup | Internal Target Group Id | None | string |
| ExternalTargetGroup |  External Target Group Id | None | string | 
| appSecurityGroupID | Application Security Group Id | None | string | 

## Resource Creation Flow Chart


![Resource Creation Flow Chart](../../../images/aws-dag-module.png)





