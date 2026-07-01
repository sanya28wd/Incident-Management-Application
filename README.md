# B2B Incident Management Application using SAP CAP and SAP Fiori Elements

A full-stack B2B incident management application built using the SAP Cloud Application Programming Model (CAP), SAP Fiori Elements, Node.js, OData V4, and SAP Business Technology Platform (SAP BTP).

This project is based on SAP’s Incident Management sample application and demonstrates how enterprise support teams can create, track, prioritize, and resolve customer-reported incidents through role-based services, structured workflows, and custom business logic.

---

## Repository Description

A cloud-native B2B incident management application built with SAP CAP, SAP Fiori Elements, Node.js, OData V4, and SAP BTP to manage customer-reported issues, support workflows, role-based services, and automated urgency classification.

---

## Project Overview

In B2B environments, companies need reliable systems to manage customer complaints, service requests, product issues, and support tickets. This application provides an enterprise-style incident management solution where customer issues can be recorded, processed, updated, and resolved through a structured workflow.

The application follows SAP CAP’s standard full-stack architecture:

- **Model Layer**: Defines business entities using CDS.
- **Service Layer**: Exposes OData services for different user roles.
- **UI Layer**: Uses SAP Fiori Elements for an enterprise-grade frontend.
- **Deployment Layer**: Supports SAP BTP and Cloud Foundry deployment.

The project helped me understand how modern enterprise applications are designed using SAP’s cloud-native development tools.

---

## Business Use Case

This application represents a B2B customer support scenario.

A customer reports an issue to a company, and a support processor creates an incident on behalf of that customer. The incident can then be assigned, updated, prioritized, and tracked until it is resolved.

This type of application is useful for companies handling:

- Customer complaints
- Product issues
- Service requests
- Enterprise client support
- Internal support workflows
- After-sales service operations

The goal is to make customer issue resolution more organized, traceable, and efficient.

---

## Key Features

- Create and manage customer incidents
- View incident details
- Update incident status
- Assign urgency levels
- Add conversation notes for each incident
- Manage customer master data
- Manage address information
- Separate processor and admin services
- Use OData V4 services for backend communication
- Generate enterprise UI using SAP Fiori Elements
- Apply dynamic filtering by customer, status, and urgency
- Support draft handling for safer data entry
- Add custom business logic for automatic urgency classification

---

## Custom Business Logic

A custom CAP handler was added to improve incident prioritization.

If an incident subject contains keywords such as `urgent`, the application automatically sets the urgency level to **High**.

Example:

```txt
Subject: Urgent issue with product delivery
Urgency: High
```

This helps support teams identify critical customer issues faster and respond more efficiently in a B2B support environment.

---

## Tech Stack

| Area | Technology |
|---|---|
| Backend Framework | SAP Cloud Application Programming Model |
| Backend Runtime | Node.js |
| Data Modeling | Core Data Services |
| Frontend | SAP Fiori Elements, SAPUI5 |
| Services | OData V4 |
| Development Environment | SAP Business Application Studio |
| Cloud Platform | SAP Business Technology Platform |
| Runtime Environment | Cloud Foundry |
| Authentication / Authorization | XSUAA, SAP Identity Services |
| Database | SQLite for local development, SAP HANA Cloud for deployment |
| Testing | npm test scripts |

---

## Project Architecture

The application follows a modular CAP-based architecture.

```txt
User Browser
    |
    v
SAP Fiori Elements UI
    |
    v
OData V4 Services
    |
    v
CAP Service Layer
    |
    v
CDS Data Model
    |
    v
Database
```

In a deployed SAP BTP environment, the architecture can include:

```txt
User Browser
    |
    v
AppRouter
    |
    v
SAP Identity Service / XSUAA
    |
    v
CAP Application
    |
    v
SAP HANA Cloud / Database
```

This structure separates the frontend, service layer, business logic, and database layer, making the application easier to maintain and scale.

---

## Project Structure

```txt
cap-sample-incidents-mgmt/
│
├── app/                  # SAP Fiori Elements frontend applications
│
├── db/                   # CDS data models
│   └── schema.cds
│
├── srv/                  # Service definitions and business logic
│   ├── admin-service.cds
│   ├── processor-service.cds
│   └── service.js
│
├── test/                 # Test files
│
├── package.json          # Project dependencies and scripts
├── xs-security.json      # Security and role configuration
└── README.md
```

---

## Main Entities

### Incidents

Stores customer-reported issues.

Typical fields include:

- Subject
- Description
- Urgency
- Status
- Customer
- Processor
- Conversation history

### Customers

Stores customer master data used in the incident management process.

### Addresses

Maintains address information linked to customers.

### Status

Stores incident status values such as:

- Open
- In Process
- Closed

### Conversation

Stores internal notes, updates, and communication history related to each incident.

---

## Services

The application uses role-based service separation.

### Processor Service

The Processor Service is designed for support processors who handle customer issues.

Processors can:

- Create incidents
- View incidents
- Update incident details
- Add conversation notes
- Track incident progress
- Work with customer-related incident data

### Admin Service

The Admin Service is designed for administrators who manage master data.

Admins can:

- Manage customers
- Manage addresses
- Maintain status values
- Perform CRUD operations on master data

This separation improves maintainability and reflects real enterprise role-based access patterns.

---

## SAP Fiori Elements UI

The frontend is generated using SAP Fiori Elements.

The UI includes:

- List Report pages
- Object Page views
- Smart tables
- Filter bars
- Value helps
- Draft handling
- Incident detail pages
- Conversation sections

SAP Fiori Elements helps generate a clean and consistent enterprise user interface using annotations and metadata from the CAP backend.

---

## Local Setup

### 1. Clone the Repository

```bash
git clone https://github.com/SAP-archive/cap-sample-incidents-mgmt.git
cd cap-sample-incidents-mgmt
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Run the Application

```bash
cds w
```

The application will usually run locally at:

```txt
http://localhost:4004
```

---

## Running the Application

After starting the application locally:

1. Open `http://localhost:4004`
2. View the available OData services
3. Open the Fiori Preview for the required entity
4. Create, view, update, and filter incident records

---

## Testing

Run the test suite using:

```bash
npm test
```

---

## Learning Outcomes

Through this project, I gained hands-on experience with:

- SAP CAP based full-stack application development
- CDS data modeling
- OData V4 service creation
- SAP Fiori Elements UI generation
- Role-based service separation
- Custom business logic using Node.js
- Draft handling in enterprise applications
- B2B customer support workflows
- SAP Business Application Studio
- SAP BTP and Cloud Foundry deployment concepts
- Debugging and testing enterprise applications

---

## Future Scope

Possible improvements include:

- Mobile support using SAP Build Apps or SAP Mobile Development Kit
- Workflow automation for incident escalation
- Email notifications for new or updated incidents
- Analytics dashboards for complaint trends and resolution time
- Machine learning based urgency prediction
- Stronger role-based access control
- Integration with SAP S/4HANA or CRM systems
- Multi-tenant SaaS support for multiple business clients
- Improved audit logs and reporting
- Real-time notification support for processors and admins

---

## Conclusion

This project demonstrates how a B2B incident management system can be built using SAP CAP, SAP Fiori Elements, and SAP BTP. It provides a structured way to manage customer support incidents, separate user roles, expose backend services through OData, and apply business logic for better prioritization.

The application helped me understand how enterprise-grade cloud applications are designed, developed, tested, and prepared for deployment in the SAP ecosystem.

---

## Author

**Sanya Wadhawan**  
B.E. Computer Science  

