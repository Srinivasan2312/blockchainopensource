# Prerequisites

## **Docker Installation**

You will need the following installed on the platform on which you will be operating, or developing on (or for), Hyperledger Fabric:

Ubuntu 18.04/16.04: [Docker](https://www.docker.com/get-docker) version Docker xx.xx.x-ce or greater is required.

You can check the version of Docker you have installed with the following command from a terminal prompt:

	docker --version

## **Kubectl**

[Follow](https://kubernetes.io/docs/tasks/tools/install-kubectl/) the link to install kubectl.

## **Why helm chart**
Kubernetes can become complex with all the objects that needs to be handled i.e pods, services, Persistent Volumes etc. Helm makes it easy, standardized and reusable, improve productivity and reduce complexity.

### ***An overview of Helm***
Most every programming language and operating system has its own package manager to help with the installation and maintenance of software. Helm provides the same basic feature set as many of the package managers you may already be familiar with, such as Debian's apt, or Python's pip.
Helm can:
Install software.
Automatically install software dependencies.
Upgrade software.
Configure software deployments.
Fetch software packages from repositories.

### ***Charts***
Helm packages are called charts, and they consist of a few YAML configuration files and some templates that are rendered into Kubernetes manifest files. Here is the basic directory structure of a chart:
```sh
package-name/
  charts/
  templates/
  Chart.yaml
  LICENSE
  README.md
  requirements.yaml
  values.yaml
```
### ***Helm Installation***

First we'll install the helm command-line utility on our local machine. Helm provides a script that handles the installation process on Linux.

Change to a writable directory and download the script from Helm's GitHub repository:

	$ cd /tmp
	$ curl https://raw.githubusercontent.com/kubernetes/helm/master/scripts/get > install-helm.sh

Make the script executable with chmod:

	$ chmod u+x install-helm.sh

At this point you can use your favorite text editor to open the script and inspect it to make sure it’s safe. When you are satisfied, run it:

	$ ./install-helm.sh

You may be prompted for your password. Provide it and press ENTER.

	Output
	helm installed into /usr/local/bin/helm
	Run 'helm init' to configure helm.

Next we will finish the installation by installing some Helm components on our cluster.

### ***helm chart in Fulcrum***
We typically rely on Kubernetes YAML files to configure Kubernetes clusters. The YAML files are there to describe everything from the way Pods need to be configured to how load balancing is done by the cluster. These yaml files is generated using helm charts.To name a few creation of networkmap, certificate creation, registering nodes,databade configuration and so on.

### ***Pros and Cons of Using Helm Charts***

The use of variables is certainly one of the major advantages of using Helm and Helm Charts. Helm Chart acts as a template for Kubernetes deployments, so you can create a template to suit your specific needs. Similar to how you can create multiple Pods for different versions of the microservice they host, you can also create different Charts for specific iterations and purposes.

There is also the fact that Helm Charts can be made incredibly flexible thanks to its use of values.yaml. You can take active steps towards moving most — if not all — of your variables to the values.yaml files and out of the template itself to allow for easier maintenance and more flexibility in updating the Charts.

The list of advantages goes on, but that doesn’t mean there are no disadvantages of using Helm Charts. For one, creating your first Helm Chart is rather complex the first time. Helm has a pretty steep learning curve and it can take some getting used to. Fortunately, there is extensive documentation from Helm to help you learn how to get things done.

## **Vault Client(If vault is to be used)**

[Follow](https://discoposse.com/2016/11/04/installing-hashicorp-vault-on-ubuntu16-04/) the link to install vault client

## **Blockchain explorer**(optional) 
To have UI view of blockchain creation and transaction details.

## **Jenkins**

Jenkins is an open source implementation of a CI server written in Java that can be used as a self-hosted option automating the build cycle for any project. It works with any programming language and for multiple platforms including Windows, Linux and macOS

### ***Why Jenkins***

Let us imagine a scenario where the complete source code of the application was built and then deployed on a test server for testing:

First, a developer commits the code to the source code repository.Meanwhile, the Jenkins server checks the repository at regular intervals 
for changes.Soon after a commit occurs, the Jenkins server detects the changes that have occurred in the source code repository.Jenkins 
will pull those changes and will start preparing a new build.If the build fails, then the pertinent team will be notified.If the build
is successful, then Jenkins deploys the build in the test server.You could configure the pipeline (the script to run) to create the build
with several steps:Prepare, test (unit and integration tests), package, publish, deploy.

After running it, Jenkins generates a feedback, if these constraints are ok, the artifact is valid.And then Jenkins notifies the
developers about the build and test results.

Jenkins will continue to check the source code repository for further changes made in the source code,and the whole process will keep on repeating (functional tests).

### ***Jenkins use in Fulcrum***
Fulcrum used jenkins pipeline to automate the process of generating chart value using ansible playbooks and pushing it to repository that is used in kubernetes to create POD for the 
application.

### ***Jenkins use in testing and ensuring code quality***
One of the basic principles of Continuous Integration is that a build should be verifiable. You have to be able to objectively determine whether a particular build is ready to proceed to the next stage of the build process, and the most convenient way to do this is to use automated tests. Without proper automated testing, you find yourself having to retain many build artifacts and test them by hand, which is hardly in the spirit of Continuous Integration so jekins provides various plugins to automate the unit and automation testing.Another important aspects is ensuring the code quality of our application which can also be done in jenkins using SonarQube. It enables developers to track code quality, which helps them to ascertain if a project is ready to be deployed in production. Further, it allows developers to continuously inspect the code, perform automatic reviews and run analysis to find code quality issues.

### ***Pros of Jenkins***
 * Jenkins is open source and free
 * Jenkins comes with a wide range of plugins
 * Jenkins integrates and works with all major tools like CVS,Subversion,Git,Kubernetes and docker
 * Jenkins is flexible
 * Jenkins comes with a decent API suite
 * Jenkins is easy to use

### ***Cons of Jenkins***
 * Unpredictable costs
 * Lack of governance
 * No collaboration features


## **About Ansible playbook**
Playbooks are a completely different way to use ansible than in ad-hoc task execution mode, and are particularly powerful.Simply put, playbooks are the basis for a really simple configuration management and multi-machine deployment system,unlike any that already exist, and one that is very well suited to deploying complex applications.Playbooks can declare configurations, but they can also orchestrate steps of any manual ordered process, even as different steps must bounce back and forth between sets of machines in particular orders. They can launch tasks synchronously or asynchronously.

Playbooks are expressed in YAML format (see YAML Syntax) and have a minimum of syntax, which intentionally tries to not be a programming language or script, but rather a model of a configuration or a process.

Each playbook is composed of one or more ‘plays’ in a list.The goal of a play is to map a group of hosts to some well defined roles, represented by things ansible calls tasks. At a basic level, a task is nothing more than a call to an ansible module. By composing a playbook of multiple ‘plays’, it is possible to orchestrate multi-machine deployments, running certain steps on all machines in the webservers group, then certain steps on the database server group, then more commands back on the webservers group, etc.

### ***Playbook and its role in Fulcrum***
playbook is used to generate value files for fulcrum deployment which in turn used in creating different kubernetes POD's.

### ***Pros of using Ansible***

* Agent-less deployment and communication
* Uses Python, which is omnipresent in Linux distros
* Excellent security using SSH / SSH2
* CLI supports almost any programming language

### ***Cons of using Ansible***
* Prone to performance issues at times
* Introspection (i.e., seeing Playbook variable values) is lacking.

## **GitOps for Kubernetes**
GitOps is a methodology of Continuous Delivery, at the heart of which is the principle that Git be used as the source of truth for declarative infrastructure and applications. In a GitOps based deployment, a pod running in the cluster watches a specific git repo that contains the set of resource manifests that should be running in the cluster. One implementation of this, and the one we have utilized in our own deployments extensively, is Weaveworks’ Flux.
The configuration of Flux is fairly simple: you provide a git endpoint that acts as the resource manifest repo of record and the secrets it needs to access this git repo and Flux will then check this repo periodically for new commits and reconcile these with the resource manifests running in the cluster.