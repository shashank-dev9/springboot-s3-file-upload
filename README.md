Spring Boot, React.js & AWS S3 - Learning Project Documentation
IMPORTANT NOTICE & CREDITS
This project is based on and adapted from the public tutorial by Amigoscode
(Spring Boot + AWS S3 File Upload Tutorial).
I used the tutorial as a learning resource, built upon it, modified parts of it,
extended logic, and restructured the project. All original ideas, patterns, and guidance belong to
Amigoscode.
This repository represents my learning journey, not original creation.

Tutorial :- https://www.youtube.com/watch?v=9i1gQ7w2V24&t=7184s
Original Repository:- https://github.com/amigoscode/full-stack-professional
-----------------------------------------------------------------------
PROJECT OVERVIEW
This project demonstrates how to build a backend system using Spring Boot and AWS S3,
with optional React frontend. It covers:
• Running PostgreSQL inside Docker
• Connecting to DB from Spring Boot
• Creating and configuring AWS IAM users
• Uploading and downloading files from S3
• Storing metadata in PostgreSQL and actual files in S3
• Designing S3 key strategies (customerId + profileImageId)
• Full Controller → Service → Repository → S3 workflow
-----------------------------------------------------------------------
TECH STACK
Backend: Java, Spring Boot, Maven
Cloud: AWS S3
Database: PostgreSQL (Docker)
Frontend (optional): React.js
-----------------------------------------------------------------------
FEATURES IMPLEMENTED
1. PostgreSQL via Docker
• Used docker-compose to run Postgres
• Connected inside container using bash + psql
• Created DB: CREATE DATABASE customer;
• Verified Spring Boot created tables
2. AWS S3 Integration
• Created IAM user
• Stored access keys in ~/.aws/credentials
• Created bucket: shashank-amigoscode-springs3-test
• Implemented putObject & getObject
• Understood S3 keys as folder-like paths
3. Customer Profile Image Functionality
• Added profileImageId column
• On upload:
- Generate random profileImageId
- Build S3 key using customerId + profileImageId
- Upload to S3
- Store profileImageId in DB
• On download:
- Fetch profileImageId from DB
- Rebuild key
- Retrieve from S3
4. API Layer
• Endpoints to create customer
• Upload profile image
• Fetch image
-----------------------------------------------------------------------
ARCHITECTURE (HIGH LEVEL)
React (optional)
↓
Spring Boot REST API
↓
CustomerService
■ ■
PostgreSQL S3Service → AWS S3 Bucket
-----------------------------------------------------------------------
RUNNING THE PROJECT
1. Start PostgreSQL
docker compose up -d
2. Connect & create db
docker exec -it postgres sh
psql -U amigoscode -d postgres
CREATE DATABASE customer;
3. Configure AWS
Store keys in ~/.aws/credentials
4. Run Spring Boot
mvn spring-boot:run
5. Optional: React
npm install
npm run dev
-----------------------------------------------------------------------
WHAT I LEARNED
• AWS S3 fundamentals
• Why images belong in S3, not DB
• Docker + Postgres workflow
• Controller → Service → Repository → S3 flow
• Key building strategies in S3
• Spring Boot configuration techniques
• Mixing JDBC & JPA
• React dev server basics
-----------------------------------------------------------------------
CREDITS
Original tutorial: Amigoscode
Purpose: Personal learning and skill building
