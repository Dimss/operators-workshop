
## Terminology sync

#### Declarative (https://en.wikipedia.org/wiki/Declarative_programming)
In computer science, declarative programming is a programming paradigm—a style of building the structure 
and elements of computer programs—that expresses the logic of a computation without describing its control flow

C example ( i++ )
K8S yaml example

apiVersion: v1
kind: bring-coffee
metadata:
  name: espresso
spec:
  actions: ["stand up", "turn left", "open a dor", "etc.."]

apiVersion: v1
kind: bring-coffee
metadata:
  name: espresso
spec:
  action: bring-coffee
  location: raanana-office, 1st floor   

#### State (https://en.wikipedia.org/wiki/State_(computer_science))
In information technology and computer science, a system is described as stateful if 
it is designed to remember preceding events or user interactions;[1] 
the remembered information is called the state of the system.

PHPSessiD example 


### Kubernetes Operators Development the A-Z tutorial 
Kubernetes provides a native way to extend its functionality by allowing you to rite your own `Controllers`, `CustomResoureDefenitions` and `CustomResrouces`
Natively, kubernetes controllers are developed with following tools. 
CoreOS Operator framework standartisize the Operators development and provide a well defined way of how the K8S Operators can be distributed and monitored. 



###  Operator framework components 
1. Operator SDK
2. Operator OLM
3. Operator Monitoring    

1. Operator SDK Slides  
2. Operator OLM Slides
3. Operator Monitoring Slides
4. S2I, OCP Native builds, offline packages
5. Operator local development
7. Validation webhooks 

### Operator development best practices 
   


  
This 4 parts tutorial will cover how to develop, build and distribute production grade K8S Operator.

Operator SKD - Let's create K8S Operators!
Before we actually jump in into creating our operators, let's understand what functianlity our Operator should cover. 
As for example, we gonna create Cloud Native static web hosting WebServer with following requirements. 

1. Our WebServer - Nginx will serve static HTML content. 
2. The Static content should be automatically added and removed from the server.

To fulfil those requirements, we'll develop two Operators 
1. WebServerOperator will take care of 
  1.1 Create Deployment 
  1.2 Create Service
  1.3 Watch on changes in websites-cm ConfigMap 
  1.4 Mount new ConfigMap into WebServer Pod
  
2. WebSiteOperator will take care of the  

We'll need the following components 
1. Nginx WebServer Deployment 
2. K8S Service for Nginx Deployment 

For the demo, we'll deploy Nginx WebServer, the deployment will includes  
For the demo porpose will develop 2 Operators.
1. 
First of all, you'll need Go[installation link] and Operator SKD[installation link] installed on your machine.
Once Go and Operator SKD is installed, let's create a new Operator project.
  


Life Cycle manager - Deploy/Generate Certificates/ Update/ 

### Prerequisites 
1. Install GO 
2. Install Operator SDK



###
We gonna create operator for §DARP  
Let's create darp-operator project
1. `cd $GOPATH/src/github.com`
2. `operator-sdk new darp-operator --vendor=true`
3. `cd darp-operator`
4. `operator-sdk add api --api-version=okto.io/v1alpha1 --kind=Darp`
5.  https://github.com/operator-framework/operator-sdk/blob/master/doc/user-guide.md#define-the-spec-and-status Define the spec and status
6. `operator-sdk generate k8s`
7. `operator-sdk generate openapi`
8. `operator-sdk add controller --api-version=okto.io/v1alpha1 --kind=Darp`

WebServerOperator 
- Deployment 
- Service
- ConfigMap with list to of WebSites ConfigMaps 

WebSites Operator
- Route 
- ConfigMap
- CR with 
  - Nginx Configuration VirtualHost
  - WebSite Content 

 





###############
 1. `controllerutil.SetControllerReference`
 1. serverDeployment, err := r.deploymentForWebServer(webServer)  new or old deployment