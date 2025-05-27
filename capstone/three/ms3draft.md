Technical Design Phase

Chris King

Master of Science in Software Development Capstone Design Specification

Grand Canyon University

Instructor: Professor Estey

0.0 (DRAFT)

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

- **Fully responsive mobile-first web application hosted at a custom domain (e.g., tars.ai)  

- **React-based frontend with real-time drawing canvas and neural network visualization  

- **WebSocket integration for live communication between client and server  
    
- **Containerized Python backend (FastAPI) deployed to the cloud (e.g., AWS, GCP, etc.)  
    
- **PyTorch-based neural network model for digit classification  
    
- **Dynamic natural language feedback component based on model confidence score  
    
- **Secure API access restricted to the frontend client domain  
    
- **Cloud-hosted inference service with logging and error handling  

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

- CI/CD pipeline for container build, test, and deploy automation  

- Environment variables for secure API key.

### Non-Functional Requirements

- **Security**:  
  - CORS restrictions to only allow frontend-originated requests  

  - Secure WebSocket (WSS) communication  

  - API authentication (if exposed for future external use)  

- **Performance**:  
  - Canvas rendering optimized with requestAnimationFrame  

  - WebSocket messages optimized to only transmit required input data  

  - Backend inference uses GPU acceleration (where available) with async responses

### Purpose of This Solution Architecture

This architecture ensures that any developer can clearly understand the data flow, component boundaries, deployment environment, and interface responsibilities. The goal is to deliver a minimal yet complete blueprint that supports scalability, real-time interaction, and rapid future extension.

**Hardware and Software Technologies**

![Technologies](<image.png>)

**Physical Solution Design**
![Solution](<image2.png>)
**Detailed Technical Design**

**General Technical Approach**

\[Describe the technical approach and design of the project. Summarize any meeting notes, brainstorming sessions, etc. that should be retained through the design of the project.\]

**Key Technical Design Decisions**

\[Document any final technical design decisions, such as framework decisions, etc. List the technology/framework, its purpose in the design, and why it was chosen. If necessary, the proper Proof of Concepts should be defined and implemented to validate the technical decision.\]

**Database ER Diagram**

\[Provide the image file of your ER database diagram.\]

**Database Dictionary**

\[Provide the Database Dictionary of your database (refer to the "MSSE-MSSD Capstone Data Dictionary Template," located on the College of Science, Engineering and Technology page in the Student Success Center).\]

**Database DDL Scripts**

\[Provide the DDL script showing all database constraints, etc.\]

**Flow Charts/Process Flows:**

\[Insert applicable flowcharts or UML activity diagrams. Flowcharts should document algorithms or workflows that will be implemented in the program.\]

**Sitemap Diagram**
![Solution](<image3.png>)


**User Interface Diagrams**
![UI1](<image4.png>)
![UI2](<image5.png>)

_Screen Definitions and Layouts_

\[Provide a draft of each user interface screen required by the system. Depending on the project, if screen definitions and layouts are not applicable, work with the instructor to define the components of the project that may replace this step.\]

**UML Diagrams**

\[Provide applicable UML Class diagrams and UML Sequence diagrams. If you have no supporting documentation, explain your rationale for why you are able to leave this section as N/A.\]

**Service API Design**

\[Fully document any third party service interface APIs being consumed or application specific service APIs being published, how to access the service, what parameters are required by the API, and the detailed JSON data format specification that could be used by a third party developer to integrate with the service and API.\]

**NFR’s (Security Design, etc.)**

\[Outline how non-functional requirements will be supported by the design.\]

_Security_

\[Discuss the security issues relevant to the system. If there are no security issues, explain why.\]

**Operational Support Design**

\[Document how the design supports monitoring and logging.\]

**Other Documentation**

\[Provide any additional drawings, storyboards, whiteboard pictures, project schedules, tasks lists, etc. that support your approach, design, and project.\]

_Reports_

\[Provide a listing of the reports the system will provide. This section can be removed if not applicable for your project.\]

**Appendix A – Technical Issue and Risk Log**

| RISK MANAGEMENT |     |     |     |     |
| --- |     |     |     |     | --- | --- | --- | --- |
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

| ISSUES LOG |     |     |     |     |     |     |     |     |
| --- |     |     |     |     |     |     |     |     | --- | --- | --- | --- | --- | --- | --- | --- |
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