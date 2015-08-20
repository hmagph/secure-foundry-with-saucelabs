# Example of an IBM Bluemix DevOps Services Toolchain integrated with Sauce Labs

# A simple pipeline with a HelloWorld Node.js application that runs tests via Sauce Labs. This is an easy way to get a pre-configured pipeline with all the environment variables set and ready to go! The Sauce Labs username and API key fields will need to be filled in with valid information before the stage will run correctly.

Press this button, to get your own copy of the sample and toolchain running in Bluemix !

[![Deploy To Bluemix](https://bluemix.net/deploy/button.png)](https://dev01.hub.jazz.net/deploy/index.html?repository=https://github.com/hmagph/secure-foundry-with-saucelabs)

## Overview 
IBM DevOps Services has a Continuous Delivery Pipeline for deploying Cloud Foundry applications, containers, and micro-services to IBM Bluemix. You can use a textual representation of a pipeline defined by a pipeline.yml file, which makes it easy to share and copy interesting pipelines. The Deploy to Bluemix button provides a simple way to clone a project that includes the source files and the Delivery Pipeline configuration. 

## The application 
Very simple java application based upon the Bluemix sample WordCounter sample app https://hub.jazz.net/project/pskhadke/WordCounter/overview that runs within a Liberty application server.  

A Dockerfile has been added to package application as a Container.  The application can be deployed as either a Cloud Foundry application or a Container on Bluemix.  

ShowResult.java has been modified so that it has a two common security issues.  This allows the application to be used to demonstrate static code scan capabilities.  

Resource files have been added to demonstrate machine translation and Globalization services in Bluemix.

To say hello: http://myroute.mydomain?name=myName
To say inject a security issue: http://myroute.mydomain?name=<img src=x onerror=alert("ha") />

## The pipeline 
An interesting pipeline that demonstrates a few more advanced delivery pipeline capabilties 

- Globalize 
    + Leverages Globalization Pipeline services on bluemix to provide machine translation of strings that can be edited and reivewed within a continuous delivery process.  IBM Globalization Delivery provides machine translation and editing capabilities that enable you to rapidly create, maintain, and revise translations for your Bluemix™ application. This extension allows for the application developer to dynamically translate property files using machine translation. The application developer can either include updated property files directly in the application package, or the application can use dynamic resource bundles for real-time lookup of strings.  
- Package Application
    + Basic ant build to package a war file that includes best available translation from the Globalization project 
- Security Scanning
    + Leverages code scan security services to inspect war archive for security vunerabilities, provides a link to a dashboard of versioned security reports that map to the versioned application archives.  
- Deploy Stage
    + Deploys the war as a Cloud Foundry application to Bluemix 

The stages are setup with slack notifications.  By simply providing a slack WebHook in the stage configuration files you can recieve notifications of just job failures, or all activity in the pipeline.  

## References 
- [Blog on continuous delivery for containers](https://developer.ibm.com/bluemix/docs/set-up-continuous-delivery-ibm-containers/)
- [IBM DevOps Services](http://hub.jazz.net)
- [IBM Bluemix](http://bluemix.net)
