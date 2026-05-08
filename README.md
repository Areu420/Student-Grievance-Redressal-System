Student Grievance Redressal Portal

🔍 Overview

The Student Grievance Redressal Portal is a full-stack blockchain-integrated complaint management system designed for educational institutions.

The platform allows students to submit grievances securely while enabling administrators and authorities to manage, monitor, escalate, and resolve complaints efficiently.

The project combines:

* Modern full-stack web development
* Secure authentication and authorization
* Real-time complaint tracking
* Automated escalation workflows
* Blockchain-based audit transparency

The system focuses on transparency, accountability, and secure grievance handling.

⸻

🏗️ System Architecture

┌─────────────┐     ┌─────────────────┐     ┌──────────────┐
│   Client    │────▶│  Express Server │────▶│ PostgreSQL   │
│ React + Vite│     │   REST API      │     │   Database   │
└─────────────┘     └────────┬────────┘     └──────────────┘
                             │
                    ┌────────▼────────┐
                    │   Blockchain    │
                    │ Hardhat + Ether │
                    │ Solidity Smart  │
                    │    Contract     │
                    └─────────────────┘

⸻

🚀 Core Features

👨‍🎓 Student Features

* Register and login securely
* Submit grievances anonymously or publicly
* Track complaint status in real time
* View complaint timelines
* Vote on public grievances
* Receive escalation and status updates
* Access notification history

🛠️ Admin Features

* Department-based complaint management
* Update grievance status
* Monitor complaint queues
* Review department statistics
* Moderate complaint workflow

🏛️ Authority Features

* View all complaints across departments
* Access escalated complaints
* Audit log monitoring
* Manage complaint lifecycle
* Track system-wide analytics

⸻

🔐 Authentication & Security

The system implements a secure JWT-based authentication and authorization workflow.

Authentication Flow

1. User registers/login through API.
2. Passwords are hashed using bcryptjs.
3. Server generates JWT tokens.
4. Tokens are verified using authentication middleware.
5. Role-based access control restricts endpoint access.

Security Features

* JWT Authentication
* Password hashing using bcrypt
* Role-Based Access Control (RBAC)
* Rate limiting protection
* Request validation middleware
* Secure API routing
* Protected complaint visibility
* Immutable blockchain audit trail

⸻

⛓️ Blockchain Integration

The project integrates Ethereum smart contracts using Hardhat and Ethers.js.

Smart Contract Features

The GrievanceRegistry.sol contract stores:

* Complaint hash
* IPFS hash references
* Complaint status updates
* Escalation records

Blockchain Benefits

* Immutable complaint tracking
* Transparent audit logs
* Tamper-resistant records
* Verifiable escalation history

Smart Contract Functions

createComplaint(hashId, ipfsHash)
updateStatus(hashId, status)
escalateComplaint(hashId)

All blockchain actions emit events for transparency.

⸻

📊 Complaint Escalation System

The platform includes an automated escalation engine using cron jobs.

Escalation Conditions

Complaints are escalated based on:

* Severity level
* SLA deadline violations
* Community impact score

Severity SLA Rules

Severity	Escalation Time
Low	5 Days
Medium	3 Days
High	2 Days
Critical	24 Hours

Impact Score Formula

Impact Score = (Upvotes - Downvotes) × Severity Weight

Complaints with high impact scores are automatically escalated.

⸻

⚙️ Tech Stack

Frontend

* React.js
* Vite
* React Router
* Axios
* Socket.io Client
* Lucide React

Backend

* Node.js
* Express.js
* Prisma ORM
* PostgreSQL
* JWT Authentication
* bcryptjs
* Socket.io
* Node Cron

Blockchain

* Solidity
* Hardhat
* Ethers.js

Cloud & Storage

* AWS S3
* Multer
* Multer-S3

⸻

📁 Project Structure

Student-Grievance-Redressal-Portal/
│
├── client/                         # React Frontend
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── context/
│   │   ├── styles/
│   │   └── App.jsx
│   ├── package.json
│   └── vite.config.js
│
├── server/                         # Express Backend
│   ├── prisma/
│   │   └── schema.prisma
│   ├── src/
│   │   ├── routes/
│   │   ├── middlewares/
│   │   ├── lib/
│   │   ├── worker.js
│   │   ├── seed.js
│   │   └── index.js
│   ├── package.json
│   └── .env
│
├── blockchain/                     # Hardhat Blockchain Project
│   ├── contracts/
│   │   └── GrievanceRegistry.sol
│   ├── scripts/
│   ├── test/
│   └── hardhat.config.js
│
└── README.md

⸻

🌐 API Endpoints

Method	Endpoint	Access
POST	/api/auth/register	Public
POST	/api/auth/login	Public
GET	/api/complaints/public	Public
POST	/api/complaints	Authenticated
GET	/api/complaints/mine	Authenticated
POST	/api/complaints/:id/vote	Authenticated
PUT	/api/complaints/:id/status	Admin / Authority
GET	/api/complaints/department	Admin
GET	/api/complaints/all	Authority
GET	/api/complaints/escalated	Authority
GET	/api/complaints/audit-log	Authority

⸻

🗄️ Database Design

The application uses PostgreSQL with Prisma ORM.

Main Tables

* User
* Department
* Complaint
* Vote
* EscalationLog

The database schema supports:

* Role management
* Complaint tracking
* Voting system
* Escalation workflows
* Audit history

⸻

🔄 Real-Time Features

Socket.io is used for:

* Real-time notifications
* Live complaint updates
* Instant status synchronization
* Dynamic dashboard refresh

⸻

▶️ Installation & Setup

1. Clone Repository

git clone <repository-url>
cd Student-Grievance-Redressal-Portal

⸻

2. Install Dependencies

Backend

cd server
npm install

Frontend

cd ../client
npm install

Blockchain

cd ../blockchain
npm install

⸻

⚙️ Environment Configuration

Backend Environment

Create .env inside the server folder.

Example:

DATABASE_URL=
JWT_SECRET=
AWS_ACCESS_KEY_ID=
AWS_SECRET_ACCESS_KEY=
AWS_BUCKET_NAME=

⸻

🗄️ Database Setup

Create PostgreSQL Database

Create a database named:

grievance

Push Prisma Schema

cd server
npm run db:push

Seed Database

npm run seed

⸻

⛓️ Blockchain Setup

Start Hardhat Node

cd blockchain
npx hardhat node

Deploy Smart Contract

npx hardhat run scripts/deploy.js --network localhost

⸻

▶️ Run Backend Server

cd server
npm run dev

⸻

▶️ Run Frontend

cd client
npm run dev

⸻

🔑 Test Credentials

Role	Email	Password
Student	student@university.edu	password
Admin	admin@university.edu	password
Authority	authority@university.edu	password

⸻

📌 Key Functionalities

Complaint Management

* Complaint submission
* Complaint categorization
* Complaint tracking
* Complaint escalation
* Complaint resolution workflow

Community Interaction

* Upvote/downvote system
* Public transparency dashboard
* Complaint impact scoring

Transparency & Auditing

* Blockchain-backed logs
* Escalation tracking
* Immutable records

⸻

⚠️ Limitations

* Requires local PostgreSQL setup
* Blockchain node must run locally
* AWS configuration required for file uploads
* Smart contracts currently configured for local Hardhat deployment

⸻

🚀 Future Improvements

Possible future enhancements:

* AI-based grievance classification
* Sentiment analysis for complaints
* Email and SMS notifications
* Cloud blockchain deployment
* Docker containerization
* Kubernetes deployment
* Analytics dashboard
* Mobile application support
* Multi-university support
* IPFS-based decentralized file storage

⸻

📌 Conclusion

The Student Grievance Redressal Portal demonstrates a complete enterprise-level full-stack application integrated with blockchain technology.

The project combines:

* Secure authentication
* Modern frontend architecture
* RESTful backend APIs
* Database management
* Blockchain integration
* Automated workflows
* Real-time communication
* Role-based access control

It provides practical exposure to building scalable, secure, and transparent complaint management systems using modern web technologies and decentralized infrastructure.
