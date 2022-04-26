---
theme: seriph
class: text-center
highlighter: shiki
lineNumbers: false
info: |
  ## Building Resilient and scalable High-Throughput Genomics workflows
drawings:
  persist: false

layout: cover
---
<!--
Thank you to BHKi and OpenScienceKE . This is my first talk and am happy to share how cloud environments can help accelerate your workflows
-->

# Building Resilient and scalable High-Throughput Genomics workflows
Efficient  orchestrating computational pipelines for complex analysis  while handling large volumes of data across heterogeneous computational environments

---

# Agenda

<!-- global-top.vue -->

* About me
* Workflow Management system
* Modularity
* Robustness
* Reproducibility
* Interoperbilty


---

# About Me

* Andrew Espira
* System engineer,icipe
*  Interested in cloud Native solutions, Observability and monitoring, distributed computing, cloud engineering 
* open source community
* Football fan 

---

# Some notes

* Feel to reach out and ask any question
* Slides & code on GitHub

---

# Workflow Management system


<v-clicks>
Automating computational analysis by linkiing together Data mananipulation/processing tasks into a cohesive pipeline

* Genomic data has turned into a large scale data generation 

* Processing the ever increasing data is driving the evolution of software to automate and parallelize analysis on hpc environments


</v-clicks>
---

# Scalability

<v-clicks>

  - Time and cost of analysis tradeof
  - How your system scales with number of parallel tasks
  - How well your system distributes tasks i.e allocate RAM and Core with requirements of tasks


</v-clicks>

---

#  Modularity

<v-clicks>

- Build a library of reusable modules
- Perform different analysis without refactoring code
- Checkpoints/breakpoints to restart your workflow at any stage of the run

</v-clicks>

---

# Robustness

<v-clicks>
 
* How your system handles reliability
   - Recovery and restart from failure
    - Hardware or network failures
    - Detecting failures from logs easily
    - Data loss 
    - Data streaming piping data to downstream analysis rather than saving on a file

</v-clicks>

---

# Reproducibility

<v-clicks>

 * Reconstruct the same workflow 
     - use of package  managers
     - Container technologies 

</v-clicks>

---

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

<v-clicks>

* CloudFormation is still the foundation
* Apps, Stacks, Constructs defined in programming languages
* CDK Toolkit synthesizes these to CloudFormation teamplates

</v-clicks>

---

# Behind the scenes - jsii

<v-clicks>

* [jsii](https://aws.github.io/jsii/)
* Allows code in any language to interact with JavaScript classes
* Library bindings include the original JS code

</v-clicks>


---

# Behind the scenes - jsii-rosetta

<v-clicks>

* How are the bindings generated?
* Enter [jsii-rosetta](https://github.com/aws/jsii/tree/main/packages/jsii-rosetta) 
* Transpiles code snippets from TypeScript to other jsii languages
* jsii makes CDK possible! (and The CDK Book!)

</v-clicks>

---

# Assets

<v-clicks>

* What about the files required to support/run?
* Lambda Handlers, Docker Images, User data
* Where to store these?
* Assets handles these

</v-clicks>

---

# Bootstrap

<v-clicks>

* Provisioning of initial resources required by CDK
* When to bootstrap?
  * Asssets
  * CFN Templates > 50kB
  * CDK Pipelines

</v-clicks>

---
clicks: 3
---
# Demo - Install CDK + Getting started

<div grid="~ cols-2 gap-x-4">

```ts {1|2|4|5-9}
npm install typescript
npm install aws-cdk 

npx cdk init app --language typescript

const bucket = new s3.Bucket(this, 'AwsUgNairobi', {
  bucketName: 'awsugnairobi-cdk-demo',
  versioned: true
});
```

<div>

<v-clicks fade :at="0">

* Install Typescript
* Install CDK Toolkit
* Initialize a new app
* Create a new bucket

</v-clicks>
</div>
</div>

---
clicks: 3
---
# Construct object signature

<div grid="~ cols-2 gap-x-4">

```ts {1|2|3|5-9}
const bucket = new s3.Bucket(
    this, 
    'AwsUgNairobi', 
    { 
      bucketName: 'awsugnairobi-cdk-demo',
      versioned: true
    }
  );
```

<div>
<v-clicks fade :at="0">

* create a new Bucket
* scope
* id: logical id of the bucket, used to uniquely identify 
* props

</v-clicks>
</div>
</div>

---

# Live demo/coding.. 

* [code at](https://github.com/SathyaBhat/talks-slides/tree/main/infra-as-code-awsug-nairobi/infra)

---

# What next?

* Interested in learning more? check:
  * Do the [AWS CDK Workshop](https://cdkworkshop.com/)
  * Watch Matt Martz's video course on [CDK Crash Course](https://www.youtube.com/watch?v=T-H4nJQyMig)
  * (self plug) Read [The CDK Book](https://thecdkbook.com)
* Check out the [Construct Hub](https://constructs.dev/)
* Experiment! 
* Talk about your experiments at [The CDK Day](https://www.cdkday.com/)

---

# Q&A, Links

* [GitHub repo (slides + code)](https://github.com/SathyaBhat/talks-slides)
* [AWS CDK](https://aws.amazon.com/cdk)
* [The CDK Book](https://www.thecdkbook.com/)
* [The CDK Day](https://www.cdkday.com/)
* Catch me on [Twitter](https://twitter.com/sathyabhat), [GitHub](https://github.com/sathyabhat), [LinkedIn](https://www.linkedin.com/in/sathyabhat/) - sathyabhat
