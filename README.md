## Elevate API Security with Cognito and WAF

This lab is provided as part of **[AWS Innovate - Modern Applications](https://aws.amazon.com/events/aws-innovate/apj/modern-apps/)**

ℹ️ You will run this lab in your own AWS account. Please follow directions at the end of the lab to remove resources to avoid future costs.

ℹ️ Let us know what you thought of this session and how we can improve the presentation experience for you in the future by completing [this event session poll](https://amazonmr.au1.qualtrics.com/jfe/form/SV_5BWPHDlxVcsRbo2?Session=HOL03) at the end of the lab. Participants who complete the surveys from AWS Innovate Online Conference will receive a gift code for USD25 in AWS credits 1, 2 & 3. AWS credits will be sent via email by November 30, 2023.

## Introduction

APIs are used for integration between applications and assist our customers in delivering new digital businesses as public APIs in partner ecosystems. Due to the public nature of these APIs, security is a top concern for all organizations who seek to develop APIs to augment their existing business models. Although API security now benefits from increased awareness and product feature coverage, application leaders must create and implement an effective API security strategy which aligns with their business needs. An example of an effective approach to secure an API is to adopt a [Zero Trust](https://aws.amazon.com/blogs/publicsector/how-to-think-about-zero-trust-architectures-on-aws/) strategy which ensures only authorized requests are permitted to access the business layer of your application. Additionally, evaluating trust at multiple layers of the architecture allows multiple checks to be performed as the API data transits through the workload.

Through the use of [AWS Cognito](https://aws.amazon.com/cognito/), it is possible to create user pools which work with your API to obtain an identity access token for the user, which can then be used to enforce authorization controls in your API layer. However, not only can legitimate users potentially expose your organization to high risk, but also attacks can come with valid credential or token. To mitigate this risk, AWS Cognito enables you to configure how long your access token will be valid and the integration of Amazon WAF in conjunction with CloudFront will allow you to add another layer of API security to achieve a strong level of protection.

In this lab we will walk you through an example scenario of securing your API at multiple layers. We will gradually tighten the security at each layer, using the following services:

* [Amazon API Gateway](https://docs.aws.amazon.com/apigateway/latest/developerguide/welcome.html) - Used for securing REST API.
* [AWS Secrets Manager](https://docs.aws.amazon.com/secretsmanager/latest/userguide/intro.html) - Used to securely store secrets.
* [Amazon CloudFront](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Introduction.html) - Used to prevent direct access to API as well as to enforce encrypted end-to-end connections to origin.
* [AWS WAF](https://docs.aws.amazon.com/waf/latest/developerguide/waf-chapter.html) - Used to protect our API by filtering, monitoring, and blocking malicious traffic.
* [Amazon Cognito](https://docs.aws.amazon.com/cognito/latest/developerguide/what-is-amazon-cognito.html) - Used to enable access control for API

## Goals

* Store and use secrets securely
* Control traffic at all layers
* Enforce encryption in transit
* Reduce attack surface
* Controlling and managing access to your API

## Prerequisites

* An [AWS account](https://portal.aws.amazon.com/gp/aws/developer/registration/index.html) that you are able to use for testing, that is not used for production or other purposes.

> [!NOTE]
> You will be billed for any applicable AWS resources used if you complete this lab that are not covered in the [AWS Free Tier](https://aws.amazon.com/free/).


## Getting Started
To start our lab, click the following link in order:

1. [Deploy the lab base infrastructure](./content/300_Multilayered_API_Security_with_Cognito_and_WAF/1_deploy_the_lab_base_infrastructure.md)
2. [Use secrets securely](./content/300_Multilayered_API_Security_with_Cognito_and_WAF/2_use_secrets_securely.md)
3. [Prevent requests from accessing API directly](./content/300_Multilayered_API_Security_with_Cognito_and_WAF/3_prevent_requests_from_accessing_API_directly.md)
4. [Application layer defense](./content/300_Multilayered_API_Security_with_Cognito_and_WAF/4_application_layer_defence.md)
5. [Contol access to API](./content/300_Multilayered_API_Security_with_Cognito_and_WAF/5_control_access_to_API.md)
6. [Tear down](./content/300_Multilayered_API_Security_with_Cognito_and_WAF/6_teardown.md)

We have included CloudFormation templates for the first few steps to get your started and build out the base lab infrstructure. For the remainder of the lab we will use further templates what will deploy addtional services such as CloudFront, WAF and Cognito to further enhance the security of the workload. The remainder of the lab will then focus on the configuration of these services to create an example API environment which is secured at multiple layers.

> [!IMPORTANT]
> For simplicity, we have used North Virginia **'us-east-1'** as the default region for this lab. Please ensure all lab interaction is completed from this region.

## License

This library is licensed under the MIT-0 License. See the LICENSE file.

# Survey

Let us know what you thought of this session and how we can improve the presentation experience for you in the future by completing [this event session poll](https://amazonmr.au1.qualtrics.com/jfe/form/SV_5BWPHDlxVcsRbo2?Session=HOL03). Participants who complete the surveys from AWS Innovate Online Conference will receive a gift code for USD25 in AWS credits 1, 2 & 3. AWS credits will be sent via email by November 30, 2023.
Note: Only registrants of AWS Innovate Online Conference who complete the surveys will receive a gift code for USD25 in AWS credits via email.

<sup>1</sup>AWS Promotional Credits Terms and conditions apply: https://aws.amazon.com/awscredits/ 

<sup>2</sup>Limited to 1 x USD25 AWS credits per participant.

<sup>3</sup>Participants will be required to provide their business email addresses to receive the gift code for AWS credits.

Click [Survey Link](https://amazonmr.au1.qualtrics.com/jfe/form/SV_5BWPHDlxVcsRbo2?Session=HOL03).