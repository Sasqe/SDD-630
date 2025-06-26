Technical Design Phase

Chris King

Master of Science in Software Development Capstone Design Specification

Grand Canyon University

Instructor: Professor Estey

1.0

05/21/2025

**ABSTRACT**

**HISTORY AND SIGNOFF SHEET**

**Change Record**

| **Date** | **Author** | **Revision Notes** |
| --- | --- | --- |
| 05/21/2025 | Chris King | Initial draft for review/discussion |
| --- | --- | --- |
|     |     |     |
| --- | --- | --- |
|     |     |     |
| --- | --- | --- |

**Overall Instructor Feedback/Comments**

**Overall Instructor Feedback/Comments**

**Integrated Instructor Feedback into Project Documentation**

☐ Yes

**Project Approval**

☐ Professor Luo (SDD-620)


**Design Introduction**

Project TARS is designed to allow users to draw digits (0–9) and observe a live visualization of a neural network as it processes the input. The app offers real-time feedback via a natural language response based on prediction confidence, and it includes system status indicators and basic model stats.

The purpose of this design is to establish a clear technical direction for the development of a responsive, educational AI application that bridges human input with machine learning interpretability. The design has been internally reviewed and aligns with the goals established in Milestone 1 and Milestone 2. Since this is a solo development project without an external stakeholder, the design is considered satisfactory by academic standards and follows industry best practices for mobile-first AI interfaces.

**Project Deliverables:**

- **_Fully responsive mobile-first web application hosted at a custom domain (e.g., tars.ai)_**  

- **_React-based frontend with real-time drawing canvas and neural network visualization_**  

- **_WebSocket integration for live communication between client and server_**  
    
- **_Containerized Python backend (FastAPI) deployed to the cloud (e.g., AWS, GCP, etc.)_**  
    
- **_PyTorch-based neural network model for digit classification_** 
    
- **_Dynamic natural language feedback component based on model confidence score_**  
    
- **_Secure API access restricted to the frontend client domain_**  
    
- **_Cloud-hosted inference service with logging and error handling_**  

- **_Technical documentation including architecture diagram, setup instructions, and usage guide_**

**Detailed High-Level Solution Design**

**Introduction**

Project TARS is a web-based application designed to visualize neural network behavior in real time. The user interface allows users to draw digits directly on a canvas, triggering a backend neural network model to process the input and return a prediction. This prediction is displayed using confidence-based natural language, enhancing interpretability.

The frontend is built using React and is fully responsive across desktop and mobile devices. It communicates with a containerized FastAPI backend over a secure WebSocket connection and RESTful API. The backend hosts a PyTorch model trained on the MNIST dataset for digit recognition. The application architecture is modular, scalable, and deployed to the cloud with a custom domain, ensuring accessibility and performance. All communication between the client and server is protected and scoped to requests from the frontend only.

This design allows for smooth real-time interaction, educational insight into AI behavior, and a visually engaging experience across platforms.

**Detailed Overview**

The proposed design for Project TARS delivers an interactive AI visualization platform through a full-stack web application. The design tightly integrates frontend interaction, real-time server communication, and neural network inference to create an educational and engaging user experience.

The frontend is developed in React and served via a static cloud host (e.g., Vercel or S3 + CloudFront) under a custom domain (tars.ai). The backend is a containerized FastAPI service deployed via Docker to a cloud provider (e.g., AWS ECS, GCP Cloud Run). The frontend communicates with the backend using WebSockets to support low-latency, bi-directional data flow during drawing interactions.

This separation of concerns between UI and model processing ensures performance, scalability, and ease of maintenance.

The following configurations will be implemented:

- DNS routing configured for the tars.ai domain  

- SSL certificate for secure HTTPS and WSS communication  

- WebSocket gateway in backend for real-time communication   

- Environment variables for secure API key.

### Non-Functional Requirements

- **Security**:  
  - CORS restrictions to only allow frontend-originated requests  

  - Secure WebSocket (WSS) communication  

  - API authentication (if exposed for future external use)  

- **Performance**:  
  - Canvas rendering optimized with CanvasJS  

  - WebSocket messages optimized to only transmit required input data in JSON 

  - Backend inference uses GPU acceleration (where available) with async responses

### Purpose of This Solution Architecture

This architecture ensures that any developer can clearly understand the data flow, component boundaries, deployment environment, and interface responsibilities. The goal is to deliver a minimal yet complete blueprint that supports scalability, real-time interaction, and rapid future extension.

**Hardware and Software Technologies**

![Technologies](<image.png>)

**Physical Solution Design**

![Solution](<image2.png>)

**Detailed Technical Design**

**General Technical Approach**

Project TARS uses a modular client-server design to support real-time digit recognition and neural network activity visualization. The frontend, built with React, features a responsive drawing canvas for user input and a decoupled visualization layer. The backend, developed in Python using FastAPI, accepts image data via REST, performs preprocessing (grayscale conversion, adaptive contrast, shape-preserving scaling), and runs inference using a CNN trained on the MNIST dataset with PyTorch.

Key decisions from brainstorming sessions:
- Use mobile-first responsive UI to support all device types.
- Separate canvas input and neural visualizer into independent components.
- Implement machine-learning techniques such as early stopping and learning rate scheduling to maximize accuracy.
- Design backend endpoints and model interfaces to support WebSocket harness.
- Build dynamic algorithms to process neural activity from various models, and display the data in a variety of ways.

These architectural choices prioritize performance, educational clarity, and cross-platform interactivity.

**Key Technical Design Decisions**

- **PyTorch (Backend – Model Training & Inference)**  
  Final decision was made to switch from TensorFlow to PyTorch due to PyTorch offering control over neural network behavior, especially during custom layer manipulation, debugging, and real-time capturing of intermediate activations. PyTorch's dynamic computation graph provided a foundation for real-time visualization.

- **ReactJS (Frontend – UI Rendering & Interactivity)**  
  ReactJS was chosen for its ability to create responsive, interactive UIs using functional components and React Hooks. Hooks simplify state and side-effect management, making it easier to coordinate live-time visual feedback tied to backend predictions and neural activity.

- **CanvasJS (Frontend – Drawing Layer)**  
  CanvasJS was selected over ThreeJS for the visualization layer due to its stability and simpler API for 2D rendering. While ThreeJS is powerful for 3D graphics, CanvasJS offered more consistent and stable performance for 2D visualization, required less computational overhead, and integrated better with mobile responsiveness.

These decisions were finalized after testing prototype implementations of each technology in isolation. PyTorch provided better neural introspection, React Hooks streamlined frontend data binding, and CanvasJS delivered more stable input rendering—all essential for our educational app’s goals.

**Database ER Diagram**
N/A

**Database Dictionary**
N/A

**Database DDL Scripts**
N/A

**Flow Charts/Process Flows:**

**Sitemap Diagram**

![Solution](<image3.png>)

**User Interface Diagrams**

![UI1](<image4.png>)
![UI2](<image5.png>)

**UML Diagrams**

No UML Class diagrams are provided because the current implementation does not utilize object-oriented class structures. The software is primarily pythonic, with math and algorithm based rendering. The project is designed using a functional and component-based architecture: the frontend uses React functional components with hooks, and the backend is built on FastAPI using function-based endpoints and PyTorch models defined as subclasses but not structured in a way that lends itself to meaningful UML class representation.

**Service API Design**
No third-party service interface APIs are currently being consumed by Project TARS.

**NFR’s (Security Design, etc.)**

The following non-functional requirements (NFRs) will be supported by the technical design of Project TARS:

- **Scalability**  
  The backend is designed as a stateless FastAPI service, enabling easy horizontal scaling with container orchestration tools like Kubernetes or AWS ECS to support concurrent users.

- **Responsiveness**  
  ReactJS with functional components and lightweight canvas rendering ensures <100ms UI responsiveness for user interactions. Backend inference is optimized for low-latency computation.

- **Cross-Device Compatibility**  
  The frontend uses responsive CSS and viewport scaling to support mobile, tablet, and desktop environments across all modern browsers.

- **Data Security**  
  API access is restricted using CORS origin checks and optional API keys. HTTPS is enforced for all frontend–backend communication to protect user data in transit.

- **Maintainability**  
  Codebase is modularized: React components are isolated, backend logic is separated by function, and PyTorch models are structured for easy refactoring and extension.

- **Availability**  
  The system can be deployed using Docker containers for redundancy and failover, ensuring high availability with minimal downtime (target: 99.9%).

- **Performance**  
  Model inference and UI rendering are optimized for speed. Backend uses efficient image preprocessing to minimize latency.

- **Accessibility**  
  The UI supports touch input, and is hosted in a custom domain that can be easily accessed in any browser, no matter what device.

- **Logging and Monitoring**  
  Backend includes structured logging of inference calls, error handling, and timing metrics. Logs can be shipped to a monitoring service (e.g., CloudWatch, ELK stack) for observability.

- **Portability**  
  The entire system is containerized using Docker and is deployable to any Docker-compatible environment, ensuring portability across development, staging, and production.


_Security_
- **API Access Control**:  
  The backend restricts access using CORS to only allow requests from `https://tars.ai`. Additional API key headers may be required for sensitive endpoints in future production environments.

- **Transport Security**:  
  All communication between the frontend and backend occurs over HTTPS to ensure encryption of user input and responses during transit.

- **Input Validation**:  
  The backend strictly validates all incoming data, including image format, size, and encoding, to prevent injection attacks or malformed payloads.

- **No Persistent Data Storage**:  
  The system does not store user images or inputs, reducing the attack surface and eliminating the risk of data breaches.

- **Infrastructure Security**:  
  Docker-based deployment ensures consistent environment configuration. In cloud deployments, access to containers, secrets, and server instances will be limited via IAM roles and security groups.

**Operational Support Design**

- **Backend Logging**:  
  FastAPI can be extended with middleware to log request/response cycles, inference times, and errors using Python’s built-in `logging` module or structured logging libraries like `loguru`.

- **Error Tracking**:  
  Integration with tools like Sentry or Rollbar can be added to capture unhandled exceptions and provide real-time error alerts.

- **Metrics and Monitoring**:  
  Prometheus exporters can be integrated into the backend to expose metrics such as request count, latency, and system health. These can be visualized using Grafana dashboards.

- **Container-Level Monitoring**:  
  When deployed via Docker, the application can be monitored using Docker logs, and container health can be tracked with orchestration tools (e.g., AWS ECS, Kubernetes).

- **Frontend Logging**:  
  Console logs can be enhanced with error boundaries in React, and logs can optionally be shipped to a backend collector for client-side issue tracing.

**Other Documentation**
N/A


**Appendix A – Technical Issue and Risk Log**

| RISK MANAGEMENT |
| **Event Risk** | **Risk Probability**<br><br>**(high, medium, low)** | **Risk Impact** | **Risk Mitigation** | **Contingency Plan** |
| --- | --- | --- | --- | --- |
| What is the risk? | What is the probability? | What is the impact if the risk occurs? | What can be done to minimize the risk? | What can be done to minimize the impact of the risk? |
| --- | --- | --- | --- | --- |
| Latency Issues with serverless backend | Medium | &nbsp;Delayed response times for users | Optimize backend performance by reducing model size, use efficient serialization formance, and cache frequently accessed data. | Pull the weights down from the cloud to perform operations locally, storing the weights and other needed data temporarily. |
| --- | --- | --- | --- | --- |
| Learning curve for 2-D/3-D rendering | High | &nbsp;Delays in visualization delivery | Focus on simpler rendering libraries before introducing more complex libraries. | Defer complex visualizations to future phases and further simplify the visualization mechanism/interface. |
| --- | --- | --- | --- | --- |
| Unauthorized API access | Low | Compromised system security | Implement strict API validation, CORS policies, and HTTPS for secure communication. | Monitor API traffic and block unauthorized IP’s. Rotate API keys regularly. |
| --- | --- | --- | --- | --- |
| Difficulty integrating frontend and backend | Low | Slower development progress | Use clear API documentation and testing tools like postman to validate endpoints before frontend integration | Allocate additional time for testing and debugging integration issues. |
| --- | --- | --- | --- | --- |
| Deployment delays for the web client or backend | Medium | Project timeline disruption | Use CI/CD pipelines to automate deployment processes and identify issues early during integration or deployment stages. | Deploy a simplified placeholder version of the client/backend to demonstrate basic functionality. |
| --- | --- | --- | --- | --- |
| High-traffic overloads backend | Low | Service outages/performance issues | Use auto-scaling features in the cloud to handle increased traffic dynamically. | Temporarily throttle incoming requests or deploy a load balancer to distribute traffic efficiently. |
| --- | --- | --- | --- | --- |

| ISSUES LOG | 
| **ID** | **Description** | **Project Impact** | **Action Plan/Resolution** | **Owner** | **Importance** | **Date Entered** | **Date to Review** | **Date Resolved** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1   | What is the issue? | How will this impact scope, schedule, and cost? | How do you intend to deal with this issue? | Who manages this issue? | &nbsp; | &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 2   | &nbsp;Docker incompatible with VMWare | &nbsp;No impact | &nbsp;Eliminate VMWare from dev stack, research devops with docker | &nbsp;Chris King | &nbsp;Low importance | &nbsp;12/21/2024 | &nbsp;12/21/2024 | &nbsp;12/23/2024 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 3   | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |

**Appendix A – External Resources**

| **GIT URL:** | _FE -_ [_https://github.com/Sasqe/tars-fe_](https://github.com/Sasqe/tars-fe)<br><br>_BE - <https://github.com/Sasqe/tars-be>_ |
| --- | --- |
| **Hosting URL:** | _N/A ._ |
| --- | --- |