# Study Guide for Certified Jenkins Engineer exam

> The outline is copied from [Certified Jenkins Engineer (CJE) 2017 Study Guide](https://www.cloudbees.com/sites/default/files/cje-study-guide-2017.pdf). The rest of information is taken from [Jenkins User Documentation](https://jenkins.io/doc/).

The Certified Jenkins Engineer (CJE) exam consists of 60 multiple-choice questions
testing knowledge of open-source Jenkins.

## Introduction

This document is intended to help you prepare for the Certified Jenkins Engineer (CJE)
exam.

The exam consists of 60 multiple-choice questions, divided into 4 sections, which will
test your skills as a Jenkins Engineer.

In this guide, you will find a list of the topics tested on the exam, links to external
references, and sample questions.

Main differences between 2016 and 2017 certification exams:

* Questions about open-source Jenkins are now based on Jenkins 2.19.4
* Pipeline related questions upgraded to the latest syntax coming with the version 2.4
of Pipeline plugin
* Open-source section includes questions on Multibranch and Pipeline Global Libraries
* Plugins covered in the exam now include only those in the "suggested" set (see below
for details)
* Questions about CJP are now based on CJP 2.7.20.2
* CJP questions now include a section about CloudBees Assurance Program

## Structure

This exam is comprised of 4 sections:

1. Key CI/CD/Jenkins concepts
1. Jenkins usage
1. Building Continuous Delivery (CD) Pipelines
1. CD-as-code best practices

All questions are based on version [2.19.4](https://jenkins.io/changelog-stable/#v2.19.4) [new] of the Jenkins core.

All questions are based on an out-of-the-box standard installation of Jenkins ("base"
Jenkins), with the default recommended plugin set installed ("Suggested plugins").

See section "Plugins" for more information.

> NOTE: On the exam, questions are presented in random order, not in sections.

## Plugins

Questions in sections 1–4 primarily cover questions about a "base" Jenkins installation,
but knowledge of the "suggested" plugins will also be covered. Candidates are expected
to know the functionality/uses of these plugins but will not be tested on detailed usage.

[new] The "suggested" plugins are the default plugins installed by the "Setup Wizard" on
a fresh new Jenkins installation. You can find the exhaustive list, bound to a fixed Jenkins version, by following this link: [Jenkins 2.19.4 suggested plugin list](https://github.com/jenkinsci/jenkins/blob/jenkins-2.19.4/core/src/main/resources/jenkins/install/platform-plugins.json).

[new] Please note that the "[Pipeline Plugin](https://plugins.jenkins.io/workflow-aggregator)" is itself an aggregation of plugins implementing the Pipeline and related features. It includes the following capabilities:

* [Pipeline Multibranch](https://wiki.jenkins-ci.org/display/JENKINS/Pipeline+Multibranch+Plugin)
* [Pipeline Shared Groovy Libraries](https://wiki.jenkins-ci.org/display/JENKINS/Pipeline+Shared+Groovy+Libraries+Plugin)
* [Pipeline Stage View](https://wiki.jenkins-ci.org/display/JENKINS/Pipeline+Stage+View+Plugin)

## Terminology

Please also note the following:

* SCM stands for “source code management” unless otherwise specified.
* Pipeline refers to the job type created by the Pipeline plugin (formerly known as the
“Workflow plugin”), except where used generically (e.g., “CD pipelines”) or in the names
of specific plugins (e.g., “Build Pipeline plugin”).
* Various UI elements in Jenkins will be referred to using the following terms:

![Rustem Certified Jenkins Engineer](https://github.com/smartrus/certified-jenkins-engineer-study-guide/blob/master/images/rustem_certified_jenkins_engineer1.png)


![Rustem Certified Jenkins Engineer](https://github.com/smartrus/certified-jenkins-engineer-study-guide/blob/master/images/rustem_certified_jenkins_engineer2.png)

![Rustem Certified Jenkins Engineer](https://github.com/smartrus/certified-jenkins-engineer-study-guide/blob/master/images/rustem_certified_jenkins_engineer3.png)

## 1. Key CI/CD/Jenkins Concepts - 18%

This topic comprises approximately 18% of the exam. Questions cover the following
topics:

* Continuous Delivery/Continuous Integration Concepts
  * Define continuous integration, continuous delivery, continuous deployment

_Continuous Integration is a software development practice where members of a team integrate their work frequently, usually each person integrates at least daily - leading to multiple integrations per day. Each integration is verified by an automated build (including test) to detect integration errors as quickly as possible. Many teams find that this approach leads to significantly reduced integration problems and allows a team to develop cohesive software more rapidly. This article is a quick overview of Continuous Integration summarizing the technique and its current usage._

_Continuous Delivery is a software development discipline where you build software in such a way that the software can be released to production at any time._

_Continuous Deployment means that every change goes through the pipeline and automatically gets put into production, resulting in many production deployments every day._

  * Difference between CI and CD

[Quora QA](https://www.quora.com/What-is-the-difference-between-continuous-integration-and-continuous-deployment)

_Continuous Integration is a core technique where everyone commits every day and code is integrated early and often. This improves frequency and reduces difficulty._

_Continuous delivery takes this a step further. This is essentially the same as CI with one crucial difference: it allows us to deploy to production with a manual step, like the tap of a button._

_What is great about this solution, is that everybody on the team can deploy; a project manager, a tester or the product owner. This is because there are no weird, secret dev-only procedures._

_If you want a 100% automated process, you need to make the jump to what is commonly called Continuous Deployment. With this in place, nobody needs to touch a button to have a working build deployed – every step is automated!_

_Continuous Integration usually refers to integrating, building, and testing code within the development environment. Continuous Delivery builds on this, dealing with the final stages required for production deployment._

  * Stages of CI and CD

_CI Practices:_

1. _Maintain a Single Source Repository._
1. _Automate the Build_
1. _Make Your Build Self-Smoke_testing_
1. _Everyone Commits To the Mainline Every Day_
1. _Every Commit Should Build the Mainline on an Integration Machine_
1. _Fix Broken Builds Immediately_
1. _Keep the Build Fast_
1. _Test in a Clone of the Production Environment_
1. _Make it Easy for Anyone to Get the Latest Executable_
1. _Everyone can see what's happening_

_CD stages:_

[A typical CI/CD pipeline explained](https://www.michielrook.nl/2018/01/typical-ci-cd-pipeline-explained/)

_The actual list of steps depends highly on the language and platform used, but typically consists of (at least) checkout, compilation and running unit tests. Some pipelines also add steps to perform code analysis and run additional tests (such as integration tests)._

![Rustem Certified Jenkins Engineer](https://github.com/smartrus/certified-jenkins-engineer-study-guide/blob/master/images/rustem_ci_cd_pipeline1.png)

_When all these steps are successful, a unique artifact is built, packaged, and published to a repository. This can be a JAR, .tar.gz file, a container image, or whatever is applicable to the chosen language and platform._

_Some pipelines deploy the generated artifact to a test environment, to run additional checks._

_Next, the artifact is deployed to staging/acceptance (or whatever you want to call it, the environment should be equivalent to production) and verified._

_Now this is where Continuous Delivery and Continuous Deployment will start to diverge. If you want to do the former, there will be a manual gate, usually in the form of a button or similar. Pressing the button is required to “promote” an artifact to production._

_When and what to promote is a choice. Promotion typically happens when a build is considered to be “good enough”. QA has run their tests, the Product Owner has signed off, etc. This means that not all artifacts make it to production!_

_Continuous Deployment gets rid of the manual gate and fully relies on automatic verification of the acceptance environment to determine whether the pipeline can continue on to production. Production, in turn, is verified in the same way._

![Rustem Certified Jenkins Engineer](https://github.com/smartrus/certified-jenkins-engineer-study-guide/blob/master/images/rustem_ci_cd_pipeline2.png)

_Automation in general, and test automation specifically, is a crucial aspect of any CI/CD process and pipeline. Automatic verification is used in all stages, to validate artifacts, deployments, etc._

_The goal of test automation is to catch known problems. Exploratory testing, usability reports, customer feedback, etc. helps us to identify the unknown issues, at which point automated tests can be adjusted to cover whatever’s been found._

  * Continuous delivery versus continuous deployment

_Continuous Delivery just means that you are able to do frequent deployments but may choose not to do it, usually due to businesses preferring a slower rate of deployment. In order to do Continuous Deployment you must be doing Continuous Delivery._

* Jobs
  * What are jobs in Jenkins?
  * Types of jobs
  * Scope of jobs
* Builds
  * What are builds in Jenkins?
  * What are build steps, triggers, artifacts, and repositories?
  * Build tools configuration
* Source Code Management
  * What are source code management systems and how are they used?
  * Cloud-based SCMs
  * Jenkins changelogs
  * Incremental updates v clean check out
  * Checking in code
  * Infrastructure-as-Code
  * Branch and Merge Strategies
* Testing
  * Benefits of testing with Jenkins
  * Define unit test, smoke test, acceptance test, automated verification/functional
tests
* Notifications
  * Types of notifications in Jenkins
  * Importance of notifications
* Distributed Builds
  * What are distributed builds?
  * Functions of masters and agents
* Plugins
  * What are plugins?
  * What is the plugin manager?
* Jenkins Rest API
  * How to interact with it
  * Why use it?
* Security
  * Authentication versus authorization
  * Matrix security
  * Definition of auditing, credentials, and other key security concepts
* Fingerprints
  * What are fingerprints?
  * How do fingerprints work?
* Artifacts
  * How to use artifacts in Jenkins
  * Storing artifacts
* Using 3rd party tools
  * How to use 3rd party tools
* Installation Wizard [new]
  * What is the Jenkins Installation Wizard?
  * How to use the Wizard?
  * Which configurations are covered by the Installation Wizard?

These online resources provide entry points to understanding the above topics:

* http://www.martinfowler.com
  * [Continuous Integration](http://www.martinfowler.com/articles/continuousIntegration.html)
  * [Continuous Delivery](http://martinfowler.com/bliki/ContinuousDelivery.html)
  * [Deployment Pipeline](http://martinfowler.com/bliki/DeploymentPipeline.html)
* http://www.informit.com
  * [CD Pipeline Anatomy](http://www.informit.com/articles/article.aspx?p=1621865&seqNum=2)
* http://devops.com
  * [What is a CD pipeline](http://devops.com/2014/07/29/continuous-delivery-pipeline/)
* https://jaxenter.com
  * [Implementing Continuous Delivery](https://jaxenter.com/implementing-continuous-delivery-117916.html)
* http://www.infoq.com
  * [Orchestrating Pipelines Jenkins](http://www.infoq.com/articles/orch-pipelines-jenkins)
* http://technologyconversations.com
  * [Continuous Delivery Introduction to Concepts and Tools](http://technologyconversations.com/2014/04/29/continuous-delivery-introduction-to-concepts-and-tools/)
* https://en.wikipedia.org
  * [Continuous delivery](https://en.wikipedia.org/wiki/Continuous_delivery)
  * [Artifact software development](https://en.wikipedia.org/wiki/Artifact_%28software_development%29)
  * [Build automation](https://en.wikipedia.org/wiki/Build_automation)
  * [Distributed version control](https://en.wikipedia.org/wiki/Distributed_version_control)
  * [List of version control software](https://en.wikipedia.org/wiki/List_of_version_control_software)
  * [Smoke testing software](https://en.wikipedia.org/wiki/Smoke_testing_(software))
* https://jenkins.io [new]
  * [Jenkins Installation and Setup](https://jenkins.io/download/) [new]
  * [Jenkins Documentation](https://jenkins.io/doc/) [new]
  * [Jenkins Pipeline](https://jenkins.io/doc/book/pipeline/) [new]
  * [Jenkins HandBook](https://jenkins.io/doc/book/) [new]
  * https://plugins.jenkins.io [new]
* https://www.safaribooksonline.com
  * [Jenkins the Definitive Guide](https://www.safaribooksonline.com/library/view/jenkins-the-definitive/9781449311155/ch05.html)
* https://wiki.jenkins-ci.org
  * [Administering Jenkins](https://wiki.jenkins-ci.org/display/JENKINS/Administering+Jenkins)
  * [Terminology](https://wiki.jenkins-ci.org/display/JENKINS/Terminology)
  * [Extreme feedback lamp switch gear style](http://jenkins-ci.org/content/extreme-feedback-lamp-switch-gear-style)
  * [Distributed builds: Offline status and retention strategy](https://wiki.jenkins-ci.org/display/JENKINS/Distributed+builds#Distributedbuilds-Offlinestatusandretentionstrategy)
  * [Remoting issue](https://wiki.jenkins-ci.org/display/JENKINS/Remoting+issue)
  * [Remote access API](https://wiki.jenkins-ci.org/display/JENKINS/Remote+access+API)
  * [Matrix based security](https://wiki.jenkins-ci.org/display/JENKINS/Matrix-based+security)
  * [Securing Jenkins](https://wiki.jenkins-ci.org/display/JENKINS/Securing+Jenkins)
  * [Quick and Simple Security](https://wiki.jenkins-ci.org/display/JENKINS/Quick+and+Simple+Security)
* http://docs.openstack.org
  * [Jenkins job builder](http://docs.openstack.org/infra/jenkins-job-builder/triggers.html)
* https://www.simple-talk.com
  * [Branching and merging](https://www.simple-talk.com/opinion/opinion-pieces/branching-and-merging-ten-pretty-good-practices/)
* http://stackoverflow.com
  * [What is unit test, integration test, smoke test, regression test?](http://stackoverflow.com/questions/520064/what-is-unit-test-integration-test-smoke-test-regression-test)
* https://www.cloudbees.com/
  * [Notifications](https://www.cloudbees.com/)
* http://searchsecurity.techtarget.com/
  * [Authentication authorization and accounting](http://searchsecurity.techtarget.com/definition/authentication-authorization-and-accounting)

## 2. Jenkins usage (features and functionality) - 23%

This topic comprises approximately 23% of the exam. Questions cover the following
topics:

* Jobs
  * Organizing jobs in Jenkins
  * Parameterized jobs
  * Usage of Freestyle/Pipeline/Matrix jobs
* Builds
  * Setting up build steps and triggers
  * Configuring build tools
  * Running scripts as part of build steps
* Source Code Management
  * Polling source code management
  * Creating hooks
  * Including version control tags and version information
* Testing
  * Testing for code coverage
  * Test reports in Jenkins
  * Displaying test results
  * Integrating with test automation tools
  * Breaking builds
* Notifications
  * Setup and usage
  * Email notifications, instant messaging
  * Alarming on notifications
* Distributed Builds
  * Setting up and running builds in parallel
  * Setting up and using SSH agents, JNLP agents, cloud agents
  * Monitoring nodes
* Plugins
  * Setting up and using Plugin Manager
  * Finding and configuring required plugins
* CI/CD
  * Using Pipeline (formerly known as “Workflow”)
  * Integrating automated deployment
  * Release management process
  * Pipeline stage behavior
* Jenkins Rest API
  * Using REST API to trigger jobs remotely, access job status, create/delete jobs
* Security
  * Setting up and using security realms
  * User database, project security, Matrix security
  * Setting up and using auditing
  * Setting up and using credentials
* Fingerprints
  * Fingerprinting jobs shared or copied between jobs
* Artifacts
  * Copying artifacts
  * Using artifacts in Jenkins
  * Artifact retention policy
* Alerts
  * Making basic updates to jobs and build scripts
  * Troubleshooting specific problems from build and test failure alerts

These online resources provide entry points to understanding the above topics:

* https://wiki.jenkins-ci.org
  * [Distributed builds](https://wiki.jenkins-ci.org/display/JENKINS/Distributed+builds)
  * [Post-initialization script](https://wiki.jenkins-ci.org/display/JENKINS/Post-initialization+script)
  * [Features controlled by system properties](https://wiki.jenkins-ci.org/display/JENKINS/Features+controlled+by+system+properties)
* http://blog.cloudbees.com
  * [Parallelism and Distributed Builds with Jenkins](https://www.cloudbees.com/blog/parallelism-and-distributed-builds-jenkins)

## 3. Building Continuous Delivery (CD) Pipelines - 16%

This topic comprises approximately 16% of the exam. Questions cover the following
topics:

* Pipeline Concepts
  * Value stream mapping for CD pipelines
  * Why create a pipeline?
  * Gates within a CD pipeline
  * How to protect centralized pipelines when multiple groups use same tools
  * Definition of binary reuse, automated deployment, multiple environments
  * Elements of your ideal CI/CD pipeline - tools
  * Key concepts in building scripts (including security/password, environment
information, etc.)
* Upstream and downstream
  * Triggering jobs from other jobs
  * Setting up the Parameterized Trigger plugin
  * Upstream/downstream jobs
* Triggering
  * Triggering Jenkins on code changes
  * Difference between push and pull
  * When to use push vs pull
* Pipeline (formerly known as “Workflow”)
  * Benefits of Pipeline vs linked jobs
  * Functionalities offered by Pipeline
  * How to use Pipeline
  * Pipeline stage view [new]
* Folders
  * How to control access to items in Jenkins with folders
  * Referencing jobs in folders
* Parameters
  * Setting up test automation in Jenkins against an uploaded executable
  * Passing parameters between jobs
  * Identifying parameters and how to use them: file parameter, string parameter
  * Jenkins CLI parameters
* Promotions
  * Promotion of a job
  * Why promote jobs?
  * How to use the Promoted Builds plugin
* Notifications
  * How to radiate information on CD pipelines to teams
* Pipeline Multibranch and Repository Scanning [new]
  * Usage of Multibranch jobs
  * Scanning GitHub and BitBucket Organization
  * Scanning basic SCM repositories
* Pipeline Global Libraries [new]
  * How to share code across Pipelines
  * Usages of the Shared Libraries
  * Interaction with Folders and Repository scanning
  * Security and Groovy sandbox

These online resources provide entry points to understanding the above topics:

* https://jenkins.io/ [new]
  * [Handbook](https://jenkins.io/doc/book/) [new]
  * [Pipeline](https://jenkins.io/doc/book/pipeline/) [new]
  * [Pipeline Global Shared Libraries](https://jenkins.io/doc/book/pipeline/shared-libraries/) [new]
  * [Pipeline Multibranch](https://jenkins.io/doc/book/pipeline/multibranch/) [new]
  * [Controlling the Flow with Stage, Lock, and Milestone](https://jenkins.io/blog/2016/10/16/stage-lock-milestone/) [new]
* https://plugin.jenkins.io/ [new]
  * [Pipeline Plugin 2.4](https://plugins.jenkins.io/workflow-aggregator#PipelinePlugin-2.4%28Sep21%2C2016%29) [new]
* [CloudBees Knowledgebase](https://support.cloudbees.com/hc/en-us)
  * [Injecting Secrets into Jenkins Build Jobs](https://support.cloudbees.com/hc/en-us/articles/203802500-Injecting-Secrets-into-Jenkins-Build-Jobs)
* https://www.cloudbees.com
  * [Credentials API Jenkins](https://www.cloudbees.com/blog/credentials-api-jenkins)
* [CloudBees Documentation](https://go.cloudbees.com/doc/index.html)
  * [List views](https://go.cloudbees.com/docs/cloudbees-documentation/cje-user-guide/index.html#_list_views?query=view)
* https://github.com
  * [confab](https://github.com/jenkinsci/jenkins/blob/3537831a42cd5b3b27a41fcde9b1f201962f38a1/core/src/main/grammar/crontab.g#L68-L71)
  * [help-spec](https://github.com/jenkinsci/jenkins/blob/3537831a42cd5b3b27a41fcde9b1f201962f38a1/core/src/main/resources/hudson/triggers/TimerTrigger/help-spec.html#L45-L46)
  * [pause and resume execution](https://github.com/jenkinsci/workflow-plugin/blob/feb5bf44573dfc9379d9551f12b0372907e787be/README.md#pause-and-resume-execution)
  * [Executor Step Test](https://github.com/jenkinsci/workflow-plugin/blob/feb5bf44573dfc9379d9551f12b0372907e787be/aggregator/src/test/java/org/jenkinsci/plugins/workflow/steps/ExecutorStepTest.java#L165-L214)
  * [Write File Step](https://github.com/jenkinsci/workflow-plugin/blob/e0263fc7275e804785e4e93054ef0f2f2945a2dc/basic-steps/src/main/resources/org/jenkinsci/plugins/workflow/steps/WriteFileStep/help.html#L1)
* http://wiki.jenkins-ci.org
  * [Jenkins CLI](https://wiki.jenkins-ci.org/display/JENKINS/Jenkins+CLI)

## 4. CD-as-Code Best Practices - 10%

This topic comprises approximately 10% of the exam. Questions cover the following
topics:

* Distributed builds architecture
* Fungible (replaceable) agents
* Master-agent connectors and protocol
* Tool installations on agents
* Cloud agents
* Traceability
* High availability

These online resources provide entry points to understanding the above topics:

* http://go.cloudbees.com
  * [Cookbook](https://go.cloudbees.com/docs/cloudbees-documentation/cookbook/book.html)
  * [Distributed Builds Architecture](https://go.cloudbees.com/docs/cloudbees-documentation/cookbook/book.html#_distributed_builds_architecture)
  * [Choosing the Right Hardware](https://go.cloudbees.com/docs/cloudbees-documentation/cookbook/book.html#_choosing_the_right_hardware_for_masters)
  * [Architecting for Scale](https://go.cloudbees.com/docs/cloudbees-documentation/cookbook/book.html#_architecting_for_scale)
  * [Pipeline as Code formerly Workflow as Code](https://go.cloudbees.com/docs/cloudbees-documentation/cookbook/book.html#pipeline-as-code)
* http://wiki.jenkins-ci.org
  * [Remoting](https://wiki.jenkins-ci.org/display/JENKINS/Remoting+issue)

## Sample Questions

1. By definition, what does a Continuous Delivery pipeline consist of?

_`A.` Backlog items_

_`B.` Artifacts_

_`C.` Stages_

_`D.` Tickets_

_`E.` Commitments_


2. You need to execute a shell script (/usr/bin/prepare-env) just before a Linux
agent is started. How do you achieve this?

_`A.` Use the "Suffix Start Agent Command" configuration option on the agent
configuration._

_`B.` Use the "Prefix Start Agent Command" configuration option on the agent
configuration._

_`C.` Configure a .profile file containing a call to /usr/bin/prepare-env in the home
directory of the OS user which runs the agent process._

_`D.` Add a shell step to each Job tied to this agent to execute the shell script._


3. Suppose you are asked to obtain the config.xml of a folder (myFolder) from a script or HTTP client using the Jenkins Remote API. The folder exists at the root of a Jenkins
master. Which URL pattern is correct for obtaining this configuration file?

_`A.` root/job/myFolder/config.xml_

_`B.` root/folder/myFolder/config.xml_

_`C.` root/myFolder/config.xml_

_`D.` root/myFolder?param=config.xml_

_`E.` root/api/getConfig?source=myFolder_


4. What architecture is recommended by the Jenkins Cookbook for a scalable Jenkins
environment?

_`A.` Distributed Builds Architecture_

_`B.` Central Master Architecture_

_`C.` Automatic Builds Architecture_

_`D.` Manual Polling Architecture_

_`E.` One-Shot Build Architecture_


5. In a Cluster Operations Job, which THREE of the following steps can be applied to a
Client Master only?

_`A.` Install Jenkins_

_`B.` Upgrade Jenkins_

_`C.` Upgrade all plugins_

_`D.` Install plugin_

_`E.` Uninstall Jenkins_


Answers to Sample Questions:

```
1. C
2. B
3. A
4. A
5. B, C, D
```
