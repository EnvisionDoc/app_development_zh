# Overview

EnvHybrid is the development framework that Envision provides to help you develop hybrid mobile applications based on EnOS (referred to as EnvHybrid framework, or framework in the rest of the announcement). The framework allows developers to develop with most traditional front-end technologies such as JavaScript, CSS, and HTML. The framework currently supports Android and iOS.

The following architecture diagram illustrates the components of the framework, these components are all available as packages on npm.

.. image:: media/frame.png

The architecture comprises the following major modules:

- Scaffold

- Basic Plugins

- App Bridge

You can build the following types of applications from the framework:

- EnOS mobile applications: which integrate with EnOS identity and access management module and are subject to the authentication and authorization policies of EnOS

- Independent mobile applications: which do not integrate with EnOS IAM, thus run independently from EnOS.

The EnvHybrid contains all the components in the above figure.
 
## Scaffold

Scaffold is the foundation of the framework from which you can quickly build your applications and solutions. The foundation provides a kernel module and includes internal plugins to accelerate your mobile application development:

- Kernel

- Internal plugins

To access the code from npm, go to @enos/mobile-envhybrid-template.

EnvHybrid offers the following features in the **Scaffold module**.


### Kernel

The core module of the EnvHybrid framework. The module translates your H5 calls to appropriate APIs of the target mobile platforms, currently, iOS and Android supported.

### Internal Plugins

Mandatory plugins for all supported platforms, provide the interface for EnvHybrid framework to communicate with components that are built on top of the framework and bind the framework to standard device APIs. The plugins enable developers to invoke native code from JavaScript.

- **Web container**： Provides a native web container for the application. 

- **Hybrid init**：The initialization module of the application. 

- **Hybrid lib**: The core module of the application. 

- **Cordova**: Provides cordova module that is used for upgrading the application. 

- **Persistent data**: To persist data that is transmitted among different web pages. 

- **Log**: Provides log service for the application. 

- **Envcontext**: Transmits parameters for web pages. 

- **Navibar**: Used for operations relevant to navigation bar. 

- **Router**: used for routing requests.
 

## Basic Plugins

Similar to the internal plugins embedded in scaffold, basic plugins provide the interface for the framework to communicate with components that are built on top of the framework and bind the framework to standard device APIs. The basic plugins bind the framework to additional features that are specific to certain mobile platforms.

EnvHybrid offers the following features in the Basic Plugins module:

- **Single container**: provides a single-mode native web container for the framework. When a web page is loaded through the container, the framework does not open a new native web page, instead, replaces the current web page and closes all pages prior to the current one. To access the code, go to @enos/mobile-plugin-single-web-container. 

- **Tabbar**: a plugin for operations related to tabs.
 

## App Bridge

App Bridge module comprises components to help you integrate with EnOS Application Framework, thereby efficiently build the EnOS mobile applications.

EnvHybrid offers the following features in the App Bridge module:

- **Fingerprint**: used for fingerprint detection. To access the code, go to @enos/mobile-plugin-fingerprint.

- **H5 SDK**: The SDK for H5. To access the SDK, go to @enos/envhybrid-utils.
 

## Reference Information
To obtain the up-to-date documentation, go to the EnOS Documentation center: https://www.envisioniot.com/documentation/

SDK: https://www.envisioniot.com/docs/app-development/en/2.0.9/sdk_overview.html

Demo: http://git.envisioncn.com/FE/mobile-framework-hybrid-demo
