---
theme: seriph
class: text-center
highlighter: shiki
lineNumbers: false
info: |
  ## Infrastructure as code and Getting Started with AWS CDK
drawings:
  persist: false

layout: cover
---
<!--
Thank you to the AWS User Group - Nairobi. I've given many talks across the globe, but this is the first time I'm talking with a UG from Africa. I'm honoured to be here.
-->

# Infrastructure as code and Getting started with AWS CDK

---

# Agenda

<!-- global-top.vue -->

* About me
* Infrastructure as Code - What, Why
* Options for Infra as Code
* Deep dive into AWS CDK
* Some examples

---

# About Me

* Sathyajith Bhat
* Site Reliability Engineer, API Platform, Adobe
* AWS Community Hero
* Author:
  * [Practical Docker with Python](https://bit.ly/practical-docker-2e) 
  * [The CDK Book](https://thecdkbook.com)
* Co-organizer, various community events
  * AWS UG BLR, AWS Community Day(India, South Asia), CDK Day

---

# Some notes

* Feel free to stop me at any time!
* Slides & code on GitHub
* Bonus at the end!

---

# Infrastructure as Code. What & Why?

<v-clicks>

* Define any cloud resource as code
* DRY (Don't Repeat Yourself)
* Automation
* Consistency
* Versioning

</v-clicks>

---

# Options for IaC

<v-clicks>

* Scripted
  * boto / requests 

* Declarative
  * Terraform, CloudFormation

* Imperative
  * CDK, Pulumi
  * Trophosphere

</v-clicks>

---

# AWS CDK

<v-clicks>

- Cloud Development Kit
- Define cloud resources using code
- Not a DSL, same language that you might be familiar with
- CDK Supports:
  - TypeScript
  - JavaScript
  - Python
  - .net
  - Go [^dev]

</v-clicks>

[^dev]: in developer preview

---

### Concepts

<v-clicks>

* App
  * Describes the entire infrastructure to be built
  * Collection of stacks

* Stack
  * Collection of constructs

* Construct
  * Heart and soul of CDK
  * Represents an abstraction of CloudFormation Resources

</v-clicks>

---
clicks: 2
---

# Constructs

<div grid="~ cols-2 gap-x-4">

```ts {1-10|12-15|17-18}
// L1 construct
const bucket = new s3.CfnBucket(this, "MyCfnBucket", {
  bucketName: "MyBucket",
  corsConfiguration: {
    corsRules: [{
          allowedOrigins: ["*"],
          allowedMethods: ["GET"]
    }]
  }
});

// L2 construct 
new s3.Bucket(this, 'MyCdkBucket', {
  versioned: true
});

// L3 construct
new NotifyingBucket(this, 'MyNotifyingBucket');
```

<div>

<v-clicks fade :at="0">

- L1: Raw CFN Resources
  - Represents a CFN resource
- L2: Curated constructs
  - Created by the CDK team to create common objects
- L3: Pattern constructs
  - Collections of constructs that define applications/org patterns

</v-clicks>

</div></div>

---

# Behind the scenes

* CloudFormation is still the foundation
* Apps, Stacks, Constructs defined in programming languages
* CDK Toolkit synthesizes these to CloudFormation teamplates

---

# Q&A, Links

* GitHub repo (slides + code)
* [AWS Fargate](https://aws.amazon.com/fargate/)
* [AWS CDK](https://aws.amazon.com/cdk)
* [The CDK Book](https://www.thecdkbook.com/)
* Catch me on [Twitter](https://twitter.com/sathyabhat), [GitHub](https://github.com/sathyabhat), [LinkedIn](https://www.linkedin.com/in/sathyabhat/) - sathyabhat
