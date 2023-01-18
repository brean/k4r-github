# knowledge4retail
## What is knowledge4retail?
Knowledge4retail is a set of container-based services to implement digital twins of retail environments. It includes tools and interfaces to create analytics applications and connect your data sources (erp systems, sensors). A kubernetes-based sample setup of the reference implementation is provided.\
The detailed functional description of the project context can be found at [https://knowledge4retail.org/](https://knowledge4retail.org/)
## Overview
This section provides information about the most important services and their purpose. Please refer the the documentation of each service for more detailed information and instructions.
### Services
#### Digital Twin
The core k4r digital twin. It provides graphql, rest and kafka interfaces to read and modify diital twins and emits notifications to the messaging bus when objects are added or changed.\
Repository: [Github](https://github.com/knowledge4retail/k4r-dt-api)\
Documentation: [Github](https://github.com/knowledge4retail/k4r-dt-api/blob/main/README.md)\
Charts: k4r-dt-api
#### Analyticgs Workflow Engine
A graphical composition tool for python-based analytical workflows. Provides an adapter to the digital twin to allow for easy creation of custom webservice-based analytical endpoints to your digital twins.\
Repository: [Github](https://github.com/hetida/hetida-designer)\
Documentation: [Github](https://github.com/hetida/hetida-designer/tree/release/docs)\
Charts: hetida-designer
#### Semantic Knowledge Processing Engine
TODO - layman explanation of what knowrob has to offer\
Repository: [Link To Repository](https://github.com/knowrob/knowrob)\
Documentation: [Link To Documentation](https://github.com/knowrob/knowrob)\
Charts: knowrob
#### ERP interface
Adapter-based webservices to connect your ERP-system to the k4r digital twin. Customize this package according to your ERP-implementation. Includes a sample-implementation for a standard SAP installation.\
Repository: [TODO - Link To Repository](https://example.com)\
Documentation: [TODO - Link To Documentation](https://example.com)\
Charts: erp-adapter, sap-erp-adapter
#### Robotics Planning Controller
Tools for managing robotic agents. It includes an own [ROSPLAN](https://kcl-planning.github.io/ROSPlan/)-instance that connects to the digital twin to create its knowledge base for planning and provides WebSocket-adapter for robots to connect to. The package offers a web application for controlling robots and an adapter to execute ROSPlan-generated plans on robotic agents like [MARLIN](https://robotik.dfki-bremen.de/en/research/robot-systems/marlin/) either on real hardware or in simulation.\
Repository: [TODO - Link To Repository](https://example.com)\
Documentation: [TODO - Link To Documentation](https://example.com)\
Charts: robotics-web, robotics-planning
#### Store Visualization Tool
A browser-based user interface to visualize your digital twins in 3D and gather information about the physical environment.
Repository: [Github](https://github.com/knowledge4retail/k4r-storeviz)\
Documentation: [Github](https://github.com/knowledge4retail/k4r-storeviz/blob/main/README.md)\
Charts: storeviz
#### Central User Interface
Offers a dashboard to automatically show information about installed K4R Services. Also provides an overview of your digital twins including a map-based view and visualizes the current state of your digital twin data model. The application is written in a way to allow for easy extension with custom functionality.\
Repository: [Github](https://github.com/knowledge4retail/k4r-portal)\
Documentation: [Github](https://github.com/knowledge4retail/k4r-portal/blob/main/README.md)\
Charts: k4r-portal, k4r-portal-backend
#### Distance Matrix Calculation
External Rest-Interface to the distance matrix hetida workflow. Calculate distances between objects in a store and use the results for route planning and similar use-cases.\
Repository: [Github](https://github.com/knowledge4retail/k4r-distance-matrix-api)\
Documentation: [Github](https://github.com/knowledge4retail/k4r-distance-matrix-api/blob/main/README.md)\
Charts: k4r-distance-matrix-api
#### RFID Decoding Service
An internal service to decode rfid tags to (s)gtin. Useful when connecting scanning sensors to the k4r platform.\
Repository: [Github](https://github.com/knowledge4retail/k4r-rfid2gtin)\
Documentation: [Github](https://github.com/knowledge4retail/k4r-rfid2gtin/blob/main/README.md)\
Charts: k4r-rfid2gtin
#### Identity Management
If you require identity-based access to your k4r-services, you can use the provided configuration to get started. Please refer to the identity management documentation for detailed instructions and alternatives.\
Repository: [Github](https://github.com/knowledge4retail/k4r-infrastructure)\
Documentation: [Github](https://github.com/knowledge4retail/k4r-docs/blob/main/identity.md)\
Charts: keycloak, oauth2-proxy
#### Messaging
K4R is setup to use Kafka to ingest updates and emit well-defined messages when digital twins change. If you do not want to provide your own installation, this package provides a working setup out of the box.\
Repository: [Github](https://github.com/knowledge4retail/k4r-infrastructure)\
Documentation: [Github](https://github.com/knowledge4retail/k4r-infrastructure/blob/main/README.md)\
Charts: kafka
## Getting started
### Requirements
To install the most basic installation of knowledge4retail, a kubernetes cluster is required.
The [helmfile-based setup routines](https://github.com/knowledge4retail/k4r-infrastructure) were tested and proven on Azure Kubernetes Services, minikube and microk8s. For productive scenarios, we strongly recommend to use managed databases (postgres, mongo) and messaging (kafka).
### Installation and setup
Pick the services you want to install and configure the helm charts in the infrastructure repository accordingly. The required dependencies for the chosen services can be determined from section "Dependency Graph" or from the infrastructure helmfile. Consider which authentication and autorization method [should be used](https://github.com/knowledge4retail/k4r-docs/blob/main/identity.md).\
Detailed installation instructions can be found at [the github repository](https://github.com/knowledge4retail/k4r-infrastructure/blob/main/README.md)
### First steps
After installation, get familiar with the installed services by navigating to the central user interface. A working dashboard will verify installation and functionality of the platform and allow you to discover the interfaces.
## Extending knowledge4retail
Creating your own services is as simple as providing a container image and deploying it next to the standard services. Please refer to the services documentations about how to interface with them. It is generally recommended not to interface with data stores directly but use the services application interfaces. The standard services are written with software architecture best practices in mind and most are easily extendable while ensuring upstream compatibility. However, in this case you are responsible for maintaining a workable forking flow.
## Support and resources
[Project Information](https://knowledge4retail.org/)\
[Functional Documentation](https://knowledge4retail.org/)\
[Security](https://github.com/knowledge4retail/k4r-docs/blob/main/security.md)\
[Identity Management](https://github.com/knowledge4retail/k4r-docs/blob/main/identity.md)\
[Data And Backup](https://github.com/knowledge4retail/k4r-docs/blob/main/data_and_backup.md)
