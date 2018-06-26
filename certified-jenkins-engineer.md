# Study Guide for Certified Jenkins Engineer exam

> The outline is copied from [Certified Jenkins Engineer (CJE) 2017 Study Guide](https://www.cloudbees.com/sites/default/files/cje-study-guide-2017.pdf). The rest of information is taken from [Jenkins User Documentation](https://jenkins.io/doc/).

_The Certified Jenkins Engineer (CJE) exam consists of 60 multiple-choice questions
testing knowledge of open-source Jenkins._

## Introduction

_This document is intended to help you prepare for the Certified Jenkins Engineer (CJE)
exam._

_The exam consists of 60 multiple-choice questions, divided into 4 sections, which will
test your skills as a Jenkins Engineer._

_In this guide, you will find a list of the topics tested on the exam, links to external
references, and sample questions._

_Main differences between 2016 and 2017 certification exams:_

* Questions about open-source Jenkins are now based on Jenkins 2.19.4
* Pipeline related questions upgraded to the latest syntax coming with the version 2.4
of Pipeline plugin
* Open-source section includes questions on Multibranch and Pipeline Global Libraries
* Plugins covered in the exam now include only those in the "suggested" set (see below
for details)
* Questions about CJP are now based on CJP 2.7.20.2
* CJP questions now include a section about CloudBees Assurance Program

## Structure

_This exam is comprised of 4 sections:_

1. Key CI/CD/Jenkins concepts
1. Jenkins usage
1. Building Continuous Delivery (CD) Pipelines
1. CD-as-code best practices

_All questions are based on version [2.19.4](https://jenkins.io/changelog-stable/#v2.19.4) [new] of the Jenkins core._

_All questions are based on an out-of-the-box standard installation of Jenkins ("base"
Jenkins), with the default recommended plugin set installed ("Suggested plugins")._

_See section "Plugins" for more information._

> NOTE: On the exam, questions are presented in random order, not in sections.

## Plugins

_Questions in sections 1–4 primarily cover questions about a "base" Jenkins installation,
but knowledge of the "suggested" plugins will also be covered. Candidates are expected
to know the functionality/uses of these plugins but will not be tested on detailed usage._

_[new] The "suggested" plugins are the default plugins installed by the "Setup Wizard" on
a fresh new Jenkins installation. You can find the exhaustive list, bound to a fixed Jenkins
version, by following this link: [Jenkins 2.19.4 suggested plugin list](https://github.com/jenkinsci/jenkins/blob/jenkins-2.19.4/core/src/main/resources/jenkins/install/platform-plugins.json)._

_[new] Please note that the "[Pipeline Plugin](https://plugins.jenkins.io/workflow-aggregator)" is itself an aggregation of plugins
implementing the Pipeline and related features. It includes the following capabilities:_

* [Pipeline Multibranch](https://wiki.jenkins-ci.org/display/JENKINS/Pipeline+Multibranch+Plugin)
* [Pipeline Shared Groovy Libraries](https://wiki.jenkins-ci.org/display/JENKINS/Pipeline+Shared+Groovy+Libraries+Plugin)
* [Pipeline Stage View](https://wiki.jenkins-ci.org/display/JENKINS/Pipeline+Stage+View+Plugin)

## Terminology

_Please also note the following:_

* SCM stands for “source code management” unless otherwise specified.
* Pipeline refers to the job type created by the Pipeline plugin (formerly known as the
“Workflow plugin”), except where used generically (e.g., “CD pipelines”) or in the names
of specific plugins (e.g., “Build Pipeline plugin”).
* Various UI elements in Jenkins will be referred to using the following terms:

![Rustem Certified Jenkins Engineer](https://github.com/smartrus/certified-jenkins-engineer-study-guide/images/rustem_certified_jenkins_engineer1.png)


![Rustem Certified Jenkins Engineer](https://github.com/smartrus/certified-jenkins-engineer-study-guide/images/rustem_certified_jenkins_engineer2.png)

![Rustem Certified Jenkins Engineer](https://github.com/smartrus/certified-jenkins-engineer-study-guide/images/rustem_certified_jenkins_engineer3.png)
