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
to obtain more information on the various (and many) tools and technologies the author suggests for further reading.

I originally started my development using Windows/Java 17 and IntelliJ but decided to move the project into Ubuntu 22.04 using WSL 2.
I still use IntelliJ on Windows but directly use my Ubuntu project...it has all been working fine (so far). 
I find this book a great read and wish my LiveProject was as helpful as this book.

Chapter 1
---------
This chapter covers the following topics (from book Summary):
* Cloud native applications are highly distributed systems that are specifically designed for and live in the cloud. 
* The cloud is an IT infrastructure provided as a commodity in terms of computing, storage, and networking resources.
* In the cloud, users pay only for the actual resources they use.
* Cloud platforms deliver their services at different levels of abstraction: infrastructure (IaaS), container (CaaS), platform (PaaS), functions (FaaS), or software (SaaS)
* Cloud native applications are horizontally scalable, loosely coupled, highly cohesive, resilient to faults, manageable, and observable
* Cloud native development is supported by automation, continuous delivery, and DevOps
* Continuous  delivery is a holistic engineering practice for delivering high-quality software quickly, reliably, and safely
* DevOps is a culture enabling collaboration among different roles to deliver business value together

Comment: 
This chapter has no coding. It was an introduction to the philosophy of cloud native application. There was A LOT of information in this chapter. 
I found myself understanding that one should approach building an application on the cloud from a totally different perspective than I assumed. I always 
went from the point of view - let me build it and worry about putting on the cloud later. No! This is not the right approach and now I can see why.

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

* I installed Docker for Windows

** Added initial IntelliJ project for the Catalog Service
** The key thing to learn in this Chapter is how to get your application to run as a docker container using minikube

This chapter required I get my Docker and Kubernetes instructions down. Luckily there are many tutorials and good
Manning books on the subject:
* Docker In Action, 2nd Edition by Jeff Nickloff and Stephen Kuenzli
* Kubernetes in Action, 2nd Edition by Marko Luksa (I actually read this book in a technical book club. This book is a great step-by-step guide.)

There are many technologies, frameworks and products mentioned in this chapter. The books covers many of them in 
the upcoming chapters. So there is quite a bit this book covers. The best news I can provide - it is detailed and
covered step-by-step.

If this book does not add a thick layer of knowledge into your toolbox then I don't know what will.

1. Spring MVC
2. Spring WebFlux
3. Project Reactor
4. Spring Cloud Stream
5. Spring Cloud Function (Azure Functions, AWS Lambda, Knative)
6. PostgreSQL
7. Spring Data JDBC
8. Spring Data R2DBC
9. Flyway
10. Redis
11. Spring Session
12. Spring Session Data Redis
13. Spring Cloud Config
14. ConfigMaps
15. Secrets
16. Spring Cloud Gateway
17. Spring Boot Actuator
18. Micrometer
19. Prometheus
20. Grafana, Grafana Tempo
21. OpenTelemetry
22. Fluent Bit
23. Loki
24. Spring Cloud Circuit Breaker
25. Resilience4J
26. OAuth 2.1, OpenID Connect
27. Spring Security
28. Keycloak
29. JUnit5
30. Testcontainers
31. Cloud Native Buildpacks
32. Docker and Kubernetes
33. Spring Native
34. GraalVM
35. GitHub Actions (covered in the next chapter)
36. GitOps
37. Argo CD
38. Angular

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

** Added Repository, Service and Controller classes. Added Exception handler and test cases 
** Added file to utilize GitHub Actions when files are commited
** Moved the project to edit, build and run on WLS (rather than on Windows)
** Note: I had a problem testing on Windows so I moved to WLS 2

**Comments**: This chapter is chock full of information. It can be overwhemling but the chapter presents everything - step-by-step. The only place I had to 
stop and google was how to [install grype](https://lindevs.com/install-grype-on-ubuntu) on Ubuntu 22.04. 
The instructions in the book did not work and the instructions on the grype web site did not work 
(I kept getting permissions issues). The surprising thing is at the time the author ran grype for vulnerabilities it returned no issues. I unfortunately 
saw many of the dependency libraries have Critical to High vulnerabilities today.  The good news is that the author anticipated this and does not have 
the build fail. 

12/22/2023 - In reading my notes, I forgot to note the use of a Record (vs. a Class) to represent a domain entity.
I am not familiar with using a Record vs. a Class. It feels more intuitive to me to use an @Entity domain class.
I will try to comment on this after my review and I complete the book. 

**Note**: This project uses Spring Boot 2.7.14 which means that if you start a new project using Spring Boot 3+ you will find you will need different imports and dependencies.

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

Interesting Links for more information
* [A Quick Guide to @TestPropertySource](https://www.baeldung.com/spring-test-property-source)
* [Spring @PropertySource annotation tutorial](https://zetcode.com/spring/propertysource/)

**Comments:** Another information packing chapter. I loved how the concepts were presented step-by-step. I was able to follow along and get everything up and running and tested.
Needless to say, so much of the material was new to me and I really appreciated how it was presented by the author. 
The book is worth it the price just for the first four chapters.

Chapter 5
---------
This chapter covers 

* how to use databases in a cloud native application
* Implementing state via persistence
* Using Spring Data JDBC
* How to test data persistence with Spring Boot and Testcontainers
* How to use Flyway to manage database change

**Comments:** This was another easy to follow chapter. I did get stuck (i.e. things did not work) but I always traced it to some typo
or mistake I made. I wish there were links to good tutorials on the many topics presented. This does remind me that many of these
books make quite a number of assumptions on the skill set you bring to the table, the big one being quite familiar with advanced Java
concepts - for me that would be functional style programming. The one area that I truly wish there was more time and attention
was testing.  I find the use of all the annotations in the test classes: @DataJdbcTest, @Import, @AutoConfigurationTestDatabae, @ActiveProfiles,
@ExtendWith, @Mock, @InjectMocks, @WebMvcTest, @MockBean, @JsonTest, @SpringBootTest a bit overwhelming! Code like this:
		```
		webTestClient
				.post()
				.uri("/books")
				.bodyValue(expectedBook)
				.exchange()
				.expectStatus().isCreated()
				.expectBody(Book.class).value(actualBook -> {
					assertThat(actualBook).isNotNull();
					assertThat(actualBook.isbn())
							.isEqualTo(expectedBook.isbn());
				});
		```
It would be nice to know where to look to know all the .<functionName> you can add. 
