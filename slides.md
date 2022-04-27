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

* Feel free to reach out and ask any question
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
<img src="https://drive.google.com/uc?id=11dxJlQrwV6juCF469DCB1-lR7ft0ilsN" class="m-10 h-70 rounded shadow" />
  


</v-clicks>
---   

#  Modularity

<v-clicks>

- Build a library of reusable modules
- Perform different analysis without refactoring code
- Checkpoints/breakpoints to restart your workflow at any stage of the run

<img src="https://drive.google.com/uc?id=1DNjzSsGEJCHFMldLjUE6C8FY_nmgWn2K" class="m-15 h-70 rounded shadow" />


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

    <img src="https://drive.google.com/uc?id=1DPPM4iSVuCJ8aHR1XJWXXEs703DS77OA" class="m-5 h-60 rounded shadow" />

</v-clicks>

---

# Reproducibility

<v-clicks>

 * Reconstruct the same workflow 
     - use of package  managers
     - Container technologies 
<img src="https://drive.google.com/uc?id=1oeWxb5C6PYleHBgZNI9LYAogcvXFBhBZ" class="m-5 h-60 rounded shadow" />  

</v-clicks>

---


# Nextflow sample batch

<div grid="~ cols-2 gap-x-4">

```ts {1-10|12-15|17-18}
// L1 construct
process.executor = 'awsbatch'
process.queue = 'my-batch-queue'
process.container = your-org/your-docker:image
aws.region = 'eu-west-1'
aws.accessKey = 'xxx'
aws.secretKey = 'yyy'

// L2 construct 
executor = 'crg'
singularity.enabled = true
process.container = "docker://nextflow/rnaseq-nf"
process.queue = 'cn-el7'
process.time = '90 min'
process.$quant.time = '4.5 h'


```

<div>

<v-clicks fade :at="0">

- L1: Define compute environments
  - defining the required computing resources and associate it to a Job Queue.
- L2:  cluster deployment
  - Defining the deployment configuration for the task to run


</v-clicks>

</div></div>

---

# Behind the scenes

<v-clicks>

* The Compute Environment allows you to define the computing resources required for a specific workload 
* The Job queue definition allows you to bind a specific task to one or more Compute Environments
* the Job definition is a template for one or more jobs in your workload.
* Job binds a Job definition to a specific Job queue and allows you to specify the actual task command to be executed in the container
<img src="https://drive.google.com/uc?id=1BITmj8SBpyR2BhZFgPlBUkfuX-TxAZ7H" class="m-5 h-60 rounded shadow" /> 

</v-clicks>

---

# Behind the scenes - Compute

<v-clicks>

* The job input and output data management is delegated to the user
* This means that if you only use Batch API/tools you will need to take care to stage the input data from a S3 bucket (or a different source) and upload the results to a persistent storage location.

<img src="https://drive.google.com/uc?id=18MOHfT-WtdnA9AHFpSW9G6v75DcRIdyn" class="m-5 h-60 rounded shadow" /> 


</v-clicks>


---

# Overall ojective

<v-clicks>

* Easy to use workflow
* Researcher/scientist abstraction from the worry of infrastucture and data management
* On demand and cost Efficient
* Run anywhere 
<img src="https://drive.google.com/uc?id=1CCht0EbJMkuSP2PAKNi9b7awb_LkBQCN" class="m-5 h-60 rounded shadow" /> 


</v-clicks>


# Sample Implementation pipeline

* [code at](https://github.com/aws-samples/aws-genomics-nextflow-workshop)

---

# What next?

* Interested in learning more? check:
  * Read [AWs Genomics whitepaper](https://aws.amazon.com/blogs/industries/whitepaper-genomics-data-transfer-analytics-and-machine-learning-using-aws-services/)
  * AWS  workshop on [Genomics ](https://catalog.us-east-1.prod.workshops.aws/workshops/8213ad51-878f-493b-8e5a-fbea22c4360c/en-US))
  * 


---

# Q&A, Links

* [GitHub repo (slides + code)](https://github.com/SathyaBhat/talks-slides)
* [AWS CDK](https://aws.amazon.com/cdk)
* [The CDK Book](https://www.thecdkbook.com/)
* [The CDK Day](https://www.cdkday.com/)
* Catch me on [Twitter](https://twitter.com/sathyabhat), [GitHub](https://github.com/sathyabhat), [LinkedIn](https://www.linkedin.com/in/sathyabhat/) - sathyabhat
