# Overview
This project is a full-stack clone of the popular accommodation booking platform AirBnB. 

The goal is to build a functional web application that allows users to:
    
    browse property listings, 
    view detailed property information, 
    complete bookings. 


## Technology Stack

    Frontend: HTML, CSS, JavaScript (React or similar framework)
    Version Control: Git and GitHub
    Design Tools: Figma for UI/UX design
    Backend:-
    Django: A high-level Python web framework used for building the RESTful API.
    Django REST Framework: Provides tools for creating and managing RESTful APIs.
    PostgreSQL: A powerful relational database used for data storage.
    GraphQL: Allows for flexible and efficient querying of data.
    Celery: For handling asynchronous tasks such as sending notifications or processing payments.
    Redis: Used for caching and session management.
    Docker: Containerization tool for consistent development and deployment environments.
    CI/CD Pipelines: Automated pipelines for testing and deploying code changes.

## Database Design:

    - Booking is done via MySQL DB API.
    - The search service has to get the data from Elastic Search, a NoSQL Database that 
        is best for its search engine functionality.
    - GraphQL: Offers a flexible and efficient query mechanism for interacting with the backend.
    - The booking service communicates with Redis and the booking database cluster to reduce the load 
        in the database also reduce the response time of API.
Users: 

    Fields: id (Primary Key), username, email, password_hash, role (host/guest)

    Relationships: One-to-many with Properties (as host), Bookings (as guest), Reviews

Properties:

    id (Primary Key), title, description, price_per_night, host_id (Foreign Key to Users), location
    
    Relationships: Many-to-one with Users (host), One-to-many with Bookings, Reviews

Bookings:

    id (Primary Key), property_id (Foreign Key to Properties), guest_id (Foreign Key to Users), check_in_date, check_out_date, total_price, status
    
    Relationships: Many-to-one with Properties and Users

Reviews

    id (Primary Key), property_id (Foreign Key to Properties), author_id (Foreign Key to Users), rating, comment, created_at
    
    Relationships: Many-to-one with Properties and Users

Payments

    id (Primary Key), booking_id (Foreign Key to Bookings), amount, payment_method, status, transaction_date
    
    Relationships: One-to-one with Bookings



##  Team Roles
| Role 	                | Responsibilities
| --------------------- | ------------------------------------------------------------------- |
| Project Manager 	    | Oversees timeline, coordinates team, manages deliverables           |
| Frontend Developers 	| Implements UI components, ensures responsive design                 |
| Backend Developers 	| Builds APIs, manages database, implements business logic            |
| Designers 	        | Creates mockups, maintains design system, ensures UX quality        |
| QA/Testers 	        | Writes test cases, performs testing, reports bugs                   |
| DevOps Engineers      | Manages deployment, CI/CD pipeline, server infrastructure           |
| Product Owner 	    | Defines requirements, prioritizes features, represents stakeholders |
| Scrum Master 	        | Facilitates agile processes, removes blockers, organizes meetings   |
| Database Administrator| Design and maintain databases, Implement data backup and recovery   |


## Feature Breakdown
User Management
Allows users to register, login, and manage their profiles. Includes authentication and authorization to ensure secure access to platform features.

Property Management
Enables hosts to create, update, and manage property listings with details like descriptions, photos, pricing, and availability.

Booking System
Facilitates the reservation process, allowing guests to book properties and hosts to manage bookings. Includes date selection, pricing calculation, and availability checks.

Review System
Allows guests to leave reviews and ratings for properties they've stayed at, helping other users make informed decisions.

Search and Filtering
Provides robust search functionality with filters for location, price range, property type, and amenities to help users find ideal accommodations.

## API Security
Authentication
JWT (JSON Web Tokens) will be implemented to securely authenticate users and maintain sessions without storing sensitive data on the server.

Authorization
Role-based access control will ensure users can only access resources and perform actions appropriate to their role (guest, host, admin).

Rate Limiting
API endpoints will have rate limiting to prevent abuse and denial-of-service attacks while maintaining service availability.

Data Validation
All API inputs will be strictly validated to prevent injection attacks and ensure data integrity.

HTTPS
All communications will be encrypted using HTTPS to protect data in transit from eavesdropping and man-in-the-middle attacks.

## CI/CD Pipeline
Continuous Integration (CI)
Automated testing and building of the application whenever code is pushed to the repository. This ensures that new changes don't break existing functionality.

Continuous Deployment (CD)
Automated deployment of the application to staging and production environments after successful CI processes, enabling rapid and reliable releases.

Tools
GitHub Actions for CI/CD workflows

Docker for containerization

AWS ECS/EKS for container orchestration

SonarQube for code quality analysis

Jest/Pytest for automated testing
