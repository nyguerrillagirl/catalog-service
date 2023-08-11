# catalog-service
Cloud Native Spring In Action repository

This repository contains the project: catalog-service which follows
the instructions in the book "Cloud Native Spring In Action" 

REASON: I started this book to primarily continue work on another repo. I enrolled in the 
Manning LiveProject - REST with Spring: Dockerized Spring Boot. Unfortunately, I did not know enough to 
follow the instructions in the latter half of this LiveProject and they recommended chapter 6 of this book.
I am making my way through the book in order to a) get to chapter 6 b) resume working on my LiveProject!

** I HIGHLY RECOMMEND THE BOOK ** 

Unlike the LiveProject this book provides step by step instructions and detailed explanations and of course links
to obtain more information on the various (and many) tools is suggests.

I originally started using Windows/Java 17 and IntelliJ but decided to move the project into Ubuntu 22.04 using WSL 2.
I still use IntelliJ but directly use my Ubuntu project...it has all been working fine (so far). I find this book a great read 
and wish my LiveProject was more helpful.

Chapter 1
---------
This chapter covers the following topics (from book Summary):
* Cloud native applications are highly distributed systems that are specifically designed for and live in the cloud. 
* The cloud is an IT infrastructure provided as a commodity in terms of computing, storage, and networking resources.
* In the cloud, users pay only for the actual resources they use.
* Cloud platforms deliver their services at different levels of abstraction: infrastructure (IaaS), container (CaaS), platform (PaaS), functions (FaaS), or software (SaaS)
* Cloud native applications are horizontally scalable, loosely coupled, highly cohesive, resilient to faults, manageable, and observable
* Cloud native development is supported by automation, continuous delivery, and DevOps
* Contintuous delivery is a holistic engineering practice for delivering high-quaility software quickly, reliably, and safely
* DevOps is a culture enabling colloboration among different roles to deliver business value together

Comment: 
This chapter has no coding. It was an introduction to the philosophy of cloud native application. There was A LOT of information in this chapter. 
I found myself understanding that one should approach building an application on the cloud from a totally different perspective than I assumed. I always 
went from the point of view - let me build it and worry about putting on the cloud later. No! This is not the right approach and know I can see why.

Chapter 2
---------
This chapter covers the following topics:
* The [15-Factor methodology](see: https://12factor.net/)
* An introduction to [Spring](https://spring.io/) and the most common functionality it provides for building Java applications
* [Spring Framework](https://spring.io/projects/spring-framework) and beans
* [Spring Boot](https://spring.io/projects/spring-boot) which provides the foundation for cloud native development
* [Container images](https://www.aquasec.com/cloud-native-academy/container-security/container-images/)
* [Docker](https://www.docker.com/)
* A Spring Boot application can be packaged as a container image with [Cloud Native Buildpacks](https://buildpacks.io/)
* Using [Kubernetes](https://kubernetes.io/) - minikube
* Kubernetes Pods
* Kubernetes Deployments
* Kubernetes Services  


** Added initial IntelliJ project for the Catalog Service

Chapter 3
---------
* A cloud native application should be tracked in its own codebase - and all its dependencies. Use tools like Gradle or Maven
* Cloud native applications use embedded services and are self-contained (hence, the use of Spring Boot)
* Tomcat is the default Spring Boot embedded server where you can configure it through properties to customize ports it listens on, connections, timeout, and threads
* The request/response interaction provided by a Servlet container for synchronous and blocking 
* API first principle
* Spring MVC, REST APIs using @RestController
* How to handle incoming REST requests (GET, POST, PUT, DELETE) and endpoints
* Controller methods declare the endpoints and operations they handle using the annotations @GetMapping, @PostMapping, @PutMapping, @DeleteMapping and @RequestMapping 
* Methods of a @RestController class can validate HTTP request body before the processing happens by applying @Valid annotation
* Adding validation contstraints using annotations like @NotBlank, @Pattern, and @Positive
* Mapping Java exceptions to HTTP status codes using a centralized @RestControllerAdvice class
* Unit tests using tools like JUnit, Mockito and AssertJ
* More targeted integration tests using [@SpringBootTest](https://reflectoring.io/spring-boot-test/)
* @WebMvcTest
* @JsonTest
* Using GitHub Actions

Added Repository, Service and Controller classes. Added Exception handler and test cases 
Added file to utilize GitHub Actions when files are commited
Moved the project to edit, build and run on WLS (rather than on Windows)
Note: I had a problem testing on Windows so I moved to WLS 2

**Comments**: This chapter is chock full of information. It can be overwhemling but the chapter presents everything - step-by-step. The only place I had to 
stop and google was how to [install grype](https://lindevs.com/install-grype-on-ubuntu) on Ubuntu 22.04. The instructions in the book did not work and the instructions on the grype web site did not work 
(I kept getting permissions issues). The surprising thing is at the time the author ran grype for vulnerabilities it returned no issues. I unfortunately 
saw many of the dependency libraries have Critical to High vulnerabilities today.  The good news is that the author anticipated this and does not have 
the build fail. 

Chapter 4
---------
This chapter covered the following topics:
* The Spring **Environment** object
* The need to NOT include configuration data in the application codebase
* The need for the cloud native application to remain immutable across different environments
* Using **Spring Cloud Config Server** and **Spring Cloud Config Client** 
* The distinction between using property file packaged with the app vs. environment variables vs. configuration service
* What are **properties** and **profiles**
* Obtaining properties from command-line arguments vs. JVM system properties vs. OS environment variable vs. configuration data files 
* Using the **@Value** annotation to inject properties
* Using **@ConfigurationProperties** annotation
* Defining and using custom properties 
* Use profiles as **feature flags** 
* How to intialize the book catalog when in "testdata" profile
* Set up a new GitHub **config-repo** to hold our application configuration data
* Create a new GitHub application **config-service** to use as our Spring Cloud Config Service
* Setting up our own Spring Cloud Config Service (that taps/uses our config-repo)
* Setting up our catalog-service application to use the Spring Cloud Config Client
* How to make the configuration client - resilient!
* How to refresh configuration at runtime - Learning to use the **Spring Boot Actuator**
* How to use **Spring Retry**

**Comments:** Another information packing chapter. I loved how the concepts were presented step-by-step. I was able to follow along and get everything up and running and tested.
Needless to say, so much of the material was new to me and I really appreciated how it was presented by the author. 
The book is worth it the price just for the first four chapters.

