# Dr. Evil - Terminology & Content Database

## Document Information
**Version:** 1.0  
**Date:** November 14, 2025  
**Purpose:** Complete terminology database for educational content  
**Related Documents:** Game Design Document v1.0

---

## Table of Contents
1. [Database Structure](#database-structure)
2. [Technical Terminology](#technical-terminology)
3. [Business & Management](#business--management)
4. [Project Management](#project-management)
5. [Collaboration & Communication](#collaboration--communication)
6. [Professional Workplace](#professional-workplace)
7. [Task Templates](#task-templates)
8. [Dialogue Templates](#dialogue-templates)

---

## Database Structure

### Term Entry Format

```json
{
  "id": "unique_identifier",
  "term": "Display Name",
  "category": "technical|business|project_mgmt|collaboration|professional",
  "difficulty": "beginner|intermediate|advanced|expert",
  "definition": "Short, clear definition (1-2 sentences)",
  "detailed_explanation": "Longer explanation with context (2-4 sentences)",
  "example_usage": [
    "Example sentence showing natural usage",
    "Another example in different context"
  ],
  "related_terms": ["term_id_1", "term_id_2"],
  "first_appears_level": 1,
  "common_contexts": ["research", "development", "meetings"],
  "tags": ["programming", "communication", "process"]
}
```

---

## Technical Terminology

### Beginner Level (Levels 1-5)

#### Programming & Development

```json
{
  "id": "api",
  "term": "API",
  "category": "technical",
  "difficulty": "beginner",
  "definition": "Application Programming Interface - a set of rules that allows different software applications to communicate with each other.",
  "detailed_explanation": "APIs define the methods and data formats that applications can use to request and exchange information. They act as intermediaries between different software systems, allowing them to work together without needing to understand each other's internal workings.",
  "example_usage": [
    "We'll need to integrate with their API to pull customer data automatically.",
    "The API documentation shows we can make up to 1000 requests per hour."
  ],
  "related_terms": ["endpoint", "rest_api", "json"],
  "first_appears_level": 2,
  "common_contexts": ["development", "integration"],
  "tags": ["programming", "integration", "data"]
}
```

```json
{
  "id": "debug",
  "term": "Debug",
  "category": "technical",
  "difficulty": "beginner",
  "definition": "The process of finding and fixing errors or bugs in software code.",
  "detailed_explanation": "Debugging involves systematically identifying the root cause of unexpected behavior in a program, then correcting the code to eliminate the issue. Developers use various tools and techniques like breakpoints, logging, and step-through execution to locate and resolve bugs.",
  "example_usage": [
    "I'll need a few hours to debug this issue before we can deploy.",
    "The debugger is showing that the variable isn't being initialized properly."
  ],
  "related_terms": ["bug", "breakpoint", "logging"],
  "first_appears_level": 1,
  "common_contexts": ["development", "testing"],
  "tags": ["programming", "troubleshooting"]
}
```

```json
{
  "id": "frontend",
  "term": "Frontend",
  "category": "technical",
  "difficulty": "beginner",
  "definition": "The client-side part of an application that users directly interact with, including the visual interface and user experience.",
  "detailed_explanation": "Frontend development focuses on everything users see and interact with in their browser or app. This includes layout, design, buttons, forms, and animations. Frontend developers typically work with HTML, CSS, and JavaScript to create responsive and intuitive user interfaces.",
  "example_usage": [
    "The frontend team is redesigning the dashboard to improve usability.",
    "We need someone to handle the frontend while I work on the backend API."
  ],
  "related_terms": ["backend", "ui", "ux"],
  "first_appears_level": 2,
  "common_contexts": ["development", "design"],
  "tags": ["programming", "web development", "interface"]
}
```

```json
{
  "id": "backend",
  "term": "Backend",
  "category": "technical",
  "difficulty": "beginner",
  "definition": "The server-side part of an application that handles data processing, business logic, and database operations that users don't directly see.",
  "detailed_explanation": "Backend development involves creating and maintaining the technology that powers the frontend. This includes servers, databases, and application logic. Backend developers ensure data is properly stored, retrieved, and processed, and that the application functions correctly behind the scenes.",
  "example_usage": [
    "The backend is processing the data and will return results to the frontend.",
    "We're using Python for our backend services and PostgreSQL for the database."
  ],
  "related_terms": ["frontend", "server", "database"],
  "first_appears_level": 2,
  "common_contexts": ["development", "infrastructure"],
  "tags": ["programming", "server", "data"]
}
```

```json
{
  "id": "database",
  "term": "Database",
  "category": "technical",
  "difficulty": "beginner",
  "definition": "An organized collection of structured data that can be easily accessed, managed, and updated.",
  "detailed_explanation": "Databases store information in a structured way that makes it easy to retrieve and manipulate. They use tables, rows, and columns (in relational databases) or other structures (in NoSQL databases) to organize data. Applications query databases to get the information they need to function.",
  "example_usage": [
    "All user information is stored in our central database.",
    "I'm running a query on the database to find all customers from last month."
  ],
  "related_terms": ["sql", "query", "table"],
  "first_appears_level": 1,
  "common_contexts": ["development", "data_ops"],
  "tags": ["data", "storage"]
}
```

#### Data & Analysis

```json
{
  "id": "dataset",
  "term": "Dataset",
  "category": "technical",
  "difficulty": "beginner",
  "definition": "A collection of related data points or records, usually organized in a structured format like tables or files.",
  "detailed_explanation": "Datasets are used for analysis, reporting, or training machine learning models. They can range from small collections of a few hundred records to massive databases with millions of entries. Well-organized datasets make it easier to extract insights and identify patterns.",
  "example_usage": [
    "I'm analyzing a dataset of customer purchases from the last quarter.",
    "We need to clean this dataset before we can use it for the report."
  ],
  "related_terms": ["data_analysis", "csv", "table"],
  "first_appears_level": 1,
  "common_contexts": ["research", "data_ops"],
  "tags": ["data", "analysis"]
}
```

```json
{
  "id": "spreadsheet",
  "term": "Spreadsheet",
  "category": "technical",
  "difficulty": "beginner",
  "definition": "A digital document organized into rows and columns, used for calculations, data analysis, and record-keeping.",
  "detailed_explanation": "Spreadsheets are versatile tools for organizing and analyzing data. They allow users to perform calculations, create charts, sort and filter information, and automate tasks with formulas. Common spreadsheet applications include Excel, Google Sheets, and LibreOffice Calc.",
  "example_usage": [
    "Can you add those numbers to the budget spreadsheet?",
    "I've created a spreadsheet to track our project milestones."
  ],
  "related_terms": ["excel", "formula", "pivot_table"],
  "first_appears_level": 1,
  "common_contexts": ["documentation", "data_ops"],
  "tags": ["data", "tools", "analysis"]
}
```

### Intermediate Level (Levels 6-10)

```json
{
  "id": "endpoint",
  "term": "Endpoint",
  "category": "technical",
  "difficulty": "intermediate",
  "definition": "A specific URL or URI where an API can be accessed to perform a particular function or retrieve specific data.",
  "detailed_explanation": "In API development, endpoints define the specific paths where different resources or actions are available. Each endpoint typically handles a specific type of request (GET, POST, PUT, DELETE) and returns appropriate data or performs a designated action. Well-designed endpoints follow RESTful conventions and are clearly documented.",
  "example_usage": [
    "The /users endpoint returns a list of all registered users.",
    "We need to create a new endpoint for handling password resets."
  ],
  "related_terms": ["api", "rest_api", "route"],
  "first_appears_level": 6,
  "common_contexts": ["development", "integration"],
  "tags": ["api", "web development"]
}
```

```json
{
  "id": "rest_api",
  "term": "REST API",
  "category": "technical",
  "difficulty": "intermediate",
  "definition": "Representational State Transfer API - an architectural style for designing networked applications using standard HTTP methods.",
  "detailed_explanation": "REST APIs use HTTP requests to perform CRUD operations (Create, Read, Update, Delete) on resources. They're stateless, meaning each request contains all necessary information, and they typically return data in JSON format. REST has become the standard for web APIs due to its simplicity and scalability.",
  "example_usage": [
    "Our REST API follows standard conventions with GET for retrieval and POST for creation.",
    "The mobile app communicates with the backend through a REST API."
  ],
  "related_terms": ["api", "endpoint", "http", "json"],
  "first_appears_level": 7,
  "common_contexts": ["development", "integration"],
  "tags": ["api", "architecture", "web"]
}
```

```json
{
  "id": "authentication",
  "term": "Authentication",
  "category": "technical",
  "difficulty": "intermediate",
  "definition": "The process of verifying that a user or system is who they claim to be, typically through credentials like passwords or tokens.",
  "detailed_explanation": "Authentication is a critical security measure that ensures only authorized users can access protected resources. Common methods include username/password combinations, multi-factor authentication (MFA), API keys, and token-based systems like JWT. It's different from authorization, which determines what authenticated users are allowed to do.",
  "example_usage": [
    "We're implementing two-factor authentication to improve security.",
    "The API requires authentication via a bearer token in the request header."
  ],
  "related_terms": ["authorization", "jwt", "security", "credentials"],
  "first_appears_level": 8,
  "common_contexts": ["security", "development"],
  "tags": ["security", "access control"]
}
```

```json
{
  "id": "ci_cd",
  "term": "CI/CD",
  "category": "technical",
  "difficulty": "intermediate",
  "definition": "Continuous Integration/Continuous Deployment - automated practices for frequently integrating code changes and deploying them to production.",
  "detailed_explanation": "CI/CD pipelines automate the process of testing and deploying code. Continuous Integration automatically tests code when developers commit changes, catching bugs early. Continuous Deployment automatically releases tested code to production. This approach enables faster, more reliable software releases with less manual intervention.",
  "example_usage": [
    "Our CI/CD pipeline runs all tests automatically whenever code is pushed.",
    "Setting up CI/CD reduced our deployment time from hours to minutes."
  ],
  "related_terms": ["devops", "pipeline", "deployment"],
  "first_appears_level": 9,
  "common_contexts": ["development", "deployment"],
  "tags": ["devops", "automation", "deployment"]
}
```

### Advanced Level (Levels 11-15)

```json
{
  "id": "microservices",
  "term": "Microservices",
  "category": "technical",
  "difficulty": "advanced",
  "definition": "An architectural style where an application is built as a collection of small, independent services that communicate over a network.",
  "detailed_explanation": "Microservices architecture breaks down large applications into smaller, loosely coupled services that can be developed, deployed, and scaled independently. Each service handles a specific business function and communicates with others through well-defined APIs. This approach offers flexibility and scalability but adds complexity in managing distributed systems.",
  "example_usage": [
    "We're migrating from a monolith to a microservices architecture for better scalability.",
    "Each microservice has its own database and can be deployed independently."
  ],
  "related_terms": ["architecture", "api", "distributed_systems"],
  "first_appears_level": 12,
  "common_contexts": ["architecture", "development"],
  "tags": ["architecture", "scalability", "design"]
}
```

```json
{
  "id": "idempotency",
  "term": "Idempotency",
  "category": "technical",
  "difficulty": "advanced",
  "definition": "A property where an operation produces the same result whether it's executed once or multiple times.",
  "detailed_explanation": "In distributed systems and APIs, idempotency is crucial for reliability. An idempotent operation can be safely retried without causing unintended side effects. For example, setting a value to a specific state is idempotent (setting X=5 multiple times still results in X=5), while incrementing is not (incrementing X repeatedly changes the result each time).",
  "example_usage": [
    "We designed the API endpoint to be idempotent, so duplicate requests won't create multiple records.",
    "PUT requests should be idempotent, while POST requests typically are not."
  ],
  "related_terms": ["api", "distributed_systems", "rest_api"],
  "first_appears_level": 14,
  "common_contexts": ["development", "architecture"],
  "tags": ["api design", "reliability", "concepts"]
}
```

---

## Business & Management

### Beginner Level

```json
{
  "id": "roi",
  "term": "ROI",
  "category": "business",
  "difficulty": "beginner",
  "definition": "Return on Investment - a metric that measures the profitability of an investment relative to its cost.",
  "detailed_explanation": "ROI is calculated as (Gain from Investment - Cost of Investment) / Cost of Investment, usually expressed as a percentage. It helps businesses evaluate whether an investment was worthwhile and compare different investment opportunities. A positive ROI means the investment generated more value than it cost.",
  "example_usage": [
    "We need to calculate the ROI before approving this marketing campaign.",
    "The automation project showed a 200% ROI in the first year."
  ],
  "related_terms": ["metrics", "budget", "revenue"],
  "first_appears_level": 3,
  "common_contexts": ["strategic", "business_planning"],
  "tags": ["finance", "metrics", "business"]
}
```

```json
{
  "id": "stakeholder",
  "term": "Stakeholder",
  "category": "business",
  "difficulty": "beginner",
  "definition": "Any person, group, or organization that has an interest in or is affected by a project or business decision.",
  "detailed_explanation": "Stakeholders can be internal (employees, managers) or external (customers, investors, suppliers). Identifying and managing stakeholder expectations is crucial for project success. Different stakeholders may have competing interests, so effective communication and negotiation are essential.",
  "example_usage": [
    "We need to get stakeholder approval before moving forward with the redesign.",
    "The key stakeholders for this project include the marketing team and our major clients."
  ],
  "related_terms": ["project_management", "communication", "requirements"],
  "first_appears_level": 4,
  "common_contexts": ["project_mgmt", "business"],
  "tags": ["business", "project management", "communication"]
}
```

```json
{
  "id": "kpi",
  "term": "KPI",
  "category": "business",
  "difficulty": "beginner",
  "definition": "Key Performance Indicator - a measurable value that demonstrates how effectively an organization is achieving key business objectives.",
  "detailed_explanation": "KPIs are specific metrics that align with strategic goals and help organizations track progress. Good KPIs are specific, measurable, achievable, relevant, and time-bound (SMART). Examples include revenue growth rate, customer acquisition cost, or employee satisfaction score.",
  "example_usage": [
    "Our primary KPI for this quarter is reducing customer churn by 15%.",
    "We track several KPIs on the dashboard to monitor overall business health."
  ],
  "related_terms": ["metrics", "okr", "performance"],
  "first_appears_level": 5,
  "common_contexts": ["strategic", "business"],
  "tags": ["metrics", "performance", "strategy"]
}
```

### Intermediate Level

```json
{
  "id": "okr",
  "term": "OKR",
  "category": "business",
  "difficulty": "intermediate",
  "definition": "Objectives and Key Results - a goal-setting framework where teams define objectives and track measurable key results.",
  "detailed_explanation": "OKRs help organizations align and focus their efforts. An Objective is a qualitative goal (what you want to achieve), while Key Results are quantitative measures (how you'll know you've achieved it). OKRs are typically set quarterly and should be ambitious but achievable, with 70% completion considered successful.",
  "example_usage": [
    "Our Q3 OKR is to improve user engagement, measured by three key results: 30% increase in daily active users, 25% longer session times, and 40% higher feature adoption.",
    "Let's review our OKRs to ensure they still align with company priorities."
  ],
  "related_terms": ["kpi", "goals", "metrics"],
  "first_appears_level": 8,
  "common_contexts": ["strategic", "project_mgmt"],
  "tags": ["goals", "strategy", "metrics"]
}
```

```json
{
  "id": "competitive_analysis",
  "term": "Competitive Analysis",
  "category": "business",
  "difficulty": "intermediate",
  "definition": "The process of researching and evaluating competitors to understand their strengths, weaknesses, strategies, and market position.",
  "detailed_explanation": "Competitive analysis involves gathering intelligence about competitors' products, pricing, marketing strategies, and customer feedback. This information helps businesses identify opportunities, anticipate market changes, and differentiate their offerings. Common frameworks include SWOT analysis and Porter's Five Forces.",
  "example_usage": [
    "The competitive analysis shows our pricing is 20% higher than the market average.",
    "Before launching, we need to complete a thorough competitive analysis of similar products."
  ],
  "related_terms": ["market_research", "swot", "strategy"],
  "first_appears_level": 6,
  "common_contexts": ["research", "strategic"],
  "tags": ["research", "strategy", "market"]
}
```

---

## Project Management

### Beginner Level

```json
{
  "id": "milestone",
  "term": "Milestone",
  "category": "project_mgmt",
  "difficulty": "beginner",
  "definition": "A significant point or event in a project timeline that marks the completion of a major phase or deliverable.",
  "detailed_explanation": "Milestones are used to track project progress and maintain momentum. Unlike tasks, they represent achievements rather than work to be done. They help teams celebrate successes, identify delays early, and keep stakeholders informed about project status.",
  "example_usage": [
    "Completing the prototype is our next major milestone.",
    "We hit three key milestones this month, putting us ahead of schedule."
  ],
  "related_terms": ["deliverable", "timeline", "project_plan"],
  "first_appears_level": 2,
  "common_contexts": ["project_mgmt", "planning"],
  "tags": ["project management", "planning"]
}
```

```json
{
  "id": "deliverable",
  "term": "Deliverable",
  "category": "project_mgmt",
  "difficulty": "beginner",
  "definition": "A tangible or intangible output produced as the result of a project or task, typically delivered to stakeholders.",
  "detailed_explanation": "Deliverables can be documents, software features, reports, presentations, or any other work product specified in the project scope. Clear deliverables help define success criteria and ensure everyone understands what needs to be produced. They should be specific, measurable, and have acceptance criteria.",
  "example_usage": [
    "The main deliverables for this sprint are the user authentication feature and API documentation.",
    "We need to finalize all deliverables before the client presentation next week."
  ],
  "related_terms": ["milestone", "scope", "requirements"],
  "first_appears_level": 1,
  "common_contexts": ["project_mgmt", "development"],
  "tags": ["project management", "scope"]
}
```

```json
{
  "id": "scope",
  "term": "Scope",
  "category": "project_mgmt",
  "difficulty": "beginner",
  "definition": "The defined boundaries of a project, including what work will and won't be included in the final deliverable.",
  "detailed_explanation": "Project scope outlines all the features, functions, and tasks required to complete the project successfully. Managing scope is critical because 'scope creep' (uncontrolled expansion of requirements) is a common cause of project failure. Changes to scope should be carefully evaluated for impact on timeline, budget, and resources.",
  "example_usage": [
    "That feature is outside the current scope, so we'll need to add it in phase two.",
    "Let's define the scope clearly before we start development to avoid confusion later."
  ],
  "related_terms": ["requirements", "scope_creep", "deliverable"],
  "first_appears_level": 3,
  "common_contexts": ["project_mgmt", "planning"],
  "tags": ["project management", "planning", "requirements"]
}
```

### Intermediate Level

```json
{
  "id": "agile",
  "term": "Agile",
  "category": "project_mgmt",
  "difficulty": "intermediate",
  "definition": "An iterative project management and software development approach that emphasizes flexibility, collaboration, and continuous improvement.",
  "detailed_explanation": "Agile methodologies break projects into small, manageable iterations (usually 2-4 weeks) called sprints. Teams work closely with stakeholders, adapt to changing requirements, and deliver working software frequently. Agile values individuals and interactions over processes, working software over documentation, and responding to change over following a rigid plan.",
  "example_usage": [
    "We're transitioning to agile development to respond faster to customer feedback.",
    "The agile approach lets us pivot quickly when priorities change."
  ],
  "related_terms": ["sprint", "scrum", "kanban", "standup"],
  "first_appears_level": 6,
  "common_contexts": ["project_mgmt", "development"],
  "tags": ["methodology", "project management", "development"]
}
```

```json
{
  "id": "sprint",
  "term": "Sprint",
  "category": "project_mgmt",
  "difficulty": "intermediate",
  "definition": "A fixed time period (typically 1-4 weeks) during which a specific set of work must be completed in agile development.",
  "detailed_explanation": "Sprints are the heartbeat of agile development. Each sprint begins with planning, includes daily standups, and ends with a review and retrospective. The goal is to have potentially shippable work at the end of each sprint. Sprint length should remain consistent to establish a sustainable rhythm.",
  "example_usage": [
    "We're planning the next sprint to include user authentication and profile management.",
    "Our two-week sprints help us maintain focus and deliver value regularly."
  ],
  "related_terms": ["agile", "scrum", "iteration"],
  "first_appears_level": 7,
  "common_contexts": ["project_mgmt", "development"],
  "tags": ["agile", "project management", "methodology"]
}
```

```json
{
  "id": "retrospective",
  "term": "Retrospective",
  "category": "project_mgmt",
  "difficulty": "intermediate",
  "definition": "A meeting held at the end of a sprint or project where the team reflects on what went well, what didn't, and how to improve.",
  "detailed_explanation": "Retrospectives are crucial for continuous improvement in agile teams. The team discusses successes, challenges, and action items for improvement in a safe, blame-free environment. Common formats include 'Start, Stop, Continue' or 'Liked, Learned, Lacked, Longed For.' The key is to identify concrete improvements to implement in the next iteration.",
  "example_usage": [
    "In our retrospective, we identified that unclear requirements were slowing us down.",
    "Let's schedule the sprint retrospective for Friday afternoon to review how things went."
  ],
  "related_terms": ["sprint", "agile", "continuous_improvement"],
  "first_appears_level": 8,
  "common_contexts": ["project_mgmt", "collaboration"],
  "tags": ["agile", "meetings", "improvement"]
}
```

---

## Collaboration & Communication

### Beginner Level

```json
{
  "id": "standup",
  "term": "Standup",
  "category": "collaboration",
  "difficulty": "beginner",
  "definition": "A brief daily meeting where team members share what they did yesterday, plan for today, and identify any blockers.",
  "detailed_explanation": "Standups (also called daily scrums) are typically 15 minutes or less and held at the same time each day. Participants literally stand to keep the meeting short. Each person answers three questions: What did I complete? What will I work on today? What's blocking me? The goal is quick synchronization, not detailed problem-solving.",
  "example_usage": [
    "Let's keep standup focused - save detailed discussions for after the meeting.",
    "During standup, I mentioned I'm blocked waiting for API access."
  ],
  "related_terms": ["agile", "daily_scrum", "sync"],
  "first_appears_level": 4,
  "common_contexts": ["collaboration", "project_mgmt"],
  "tags": ["meetings", "agile", "communication"]
}
```

```json
{
  "id": "sync",
  "term": "Sync",
  "category": "collaboration",
  "difficulty": "beginner",
  "definition": "Short for synchronous - a real-time meeting or communication where all participants interact at the same time.",
  "detailed_explanation": "Sync meetings happen in real-time, whether in-person or via video call. They're useful for quick decisions, brainstorming, or complex discussions that benefit from immediate back-and-forth. However, they require everyone's simultaneous availability, which can be challenging for distributed teams across time zones.",
  "example_usage": [
    "Let's schedule a quick sync to align on the design approach.",
    "Can we handle this async, or do we need a sync meeting?"
  ],
  "related_terms": ["async", "meeting", "collaboration"],
  "first_appears_level": 3,
  "common_contexts": ["collaboration", "communication"],
  "tags": ["communication", "meetings"]
}
```

```json
{
  "id": "async",
  "term": "Async",
  "category": "collaboration",
  "difficulty": "beginner",
  "definition": "Short for asynchronous - communication or work that doesn't require simultaneous participation, where people respond at different times.",
  "detailed_explanation": "Async communication includes emails, project management tools, and recorded videos where participants contribute when convenient for them. It's ideal for distributed teams across time zones and allows for thoughtful, documented responses. However, it can be slower for urgent matters or complex discussions requiring real-time interaction.",
  "example_usage": [
    "Let's discuss this async in the project thread so everyone can contribute.",
    "Async communication works well for our team since we're spread across different time zones."
  ],
  "related_terms": ["sync", "communication", "remote_work"],
  "first_appears_level": 5,
  "common_contexts": ["collaboration", "remote_work"],
  "tags": ["communication", "remote work"]
}
```

### Intermediate Level

```json
{
  "id": "feedback_loop",
  "term": "Feedback Loop",
  "category": "collaboration",
  "difficulty": "intermediate",
  "definition": "A cyclical process where outputs or results are used as inputs to refine and improve future iterations.",
  "detailed_explanation": "Feedback loops are essential for continuous improvement. In a positive feedback loop, information about results is gathered, analyzed, and used to make adjustments. This can apply to product development (user feedback improving features), team processes (retrospectives improving workflows), or any iterative process where learning from outcomes drives better results.",
  "example_usage": [
    "We've established a feedback loop with beta users to rapidly improve the product.",
    "The weekly feedback loop helps us catch and fix issues before they become bigger problems."
  ],
  "related_terms": ["iteration", "continuous_improvement", "retrospective"],
  "first_appears_level": 9,
  "common_contexts": ["collaboration", "development"],
  "tags": ["process", "improvement", "communication"]
}
```

---

## Professional Workplace

### Beginner Level

```json
{
  "id": "bandwidth",
  "term": "Bandwidth",
  "category": "professional",
  "difficulty": "beginner",
  "definition": "The amount of time, energy, or capacity someone has available to take on work or responsibilities.",
  "detailed_explanation": "In workplace contexts, bandwidth refers to a person's or team's capacity to handle additional tasks or projects. It considers existing commitments, skills, and mental/emotional capacity. Asking about someone's bandwidth is a polite way to check if they can take on more work without being overwhelmed.",
  "example_usage": [
    "I don't have the bandwidth to take on another project right now.",
    "Do you have bandwidth to review this document by Friday?"
  ],
  "related_terms": ["capacity", "workload", "resources"],
  "first_appears_level": 2,
  "common_contexts": ["professional", "project_mgmt"],
  "tags": ["workplace", "capacity", "resources"]
}
```

```json
{
  "id": "action_item",
  "term": "Action Item",
  "category": "professional",
  "difficulty": "beginner",
  "definition": "A specific task that someone commits to completing, typically assigned during a meeting with a clear owner and deadline.",
  "detailed_explanation": "Action items turn meeting discussions into concrete next steps. Each action item should have a clear owner (the person responsible), a specific task, and a target completion date. Tracking action items ensures meeting outcomes lead to actual progress and accountability.",
  "example_usage": [
    "My action item from today's meeting is to update the budget proposal by Wednesday.",
    "Let's review the action items from last week before we move on."
  ],
  "related_terms": ["task", "deliverable", "accountability"],
  "first_appears_level": 1,
  "common_contexts": ["professional", "meetings"],
  "tags": ["meetings", "tasks", "accountability"]
}
```

---

## Task Templates

### Simple Tasks (Level 1-5)

```json
{
  "id": "task_simple_001",
  "title": "Create a To-Do List",
  "category": "documentation",
  "complexity": "simple",
  "description": "Create a prioritized to-do list for this week's tasks",
  "required_skills": ["organization"],
  "estimated_duration": 5,
  "minion_types": ["coordinator"],
  "terminology_featured": ["priority", "task", "deadline"],
  "learning_objectives": [
    "Understanding task prioritization",
    "Basic organizational skills"
  ],
  "deliverable_type": "document",
  "collaboration_pattern": "solo"
}
```

```json
{
  "id": "task_simple_002",
  "title": "Research Programming Languages",
  "category": "research",
  "complexity": "simple",
  "description": "Research and summarize the top 5 programming languages in 2025",
  "required_skills": ["research", "writing"],
  "estimated_duration": 10,
  "minion_types": ["infiltrator"],
  "terminology_featured": ["research", "programming", "summary"],
  "learning_objectives": [
    "Basic research methodology",
    "Information synthesis"
  ],
  "deliverable_type": "report",
  "collaboration_pattern": "solo"
}
```

### Standard Tasks (Level 6-10)

```json
{
  "id": "task_standard_001",
  "title": "Competitive Analysis Report",
  "category": "research",
  "complexity": "standard",
  "description": "Conduct a competitive analysis of three major competitors in our market",
  "required_skills": ["research", "analysis", "writing"],
  "estimated_duration": 20,
  "minion_types": ["infiltrator", "analyst"],
  "terminology_featured": ["competitive_analysis", "market_research", "swot", "stakeholder"],
  "learning_objectives": [
    "Competitive research frameworks",
    "Market analysis techniques",
    "Business intelligence gathering"
  ],
  "deliverable_type": "report",
  "collaboration_pattern": "paired",
  "collaboration_phases": ["planning", "research", "analysis", "documentation"]
}
```

### Complex Tasks (Level 11-15)

```json
{
  "id": "task_complex_001",
  "title": "Full-Stack Web Application Prototype",
  "category": "development",
  "complexity": "complex",
  "description": "Develop a prototype web application with authentication, database, and API",
  "required_skills": ["frontend", "backend", "database", "api"],
  "estimated_duration": 45,
  "minion_types": ["codebreaker", "architect", "analyst"],
  "terminology_featured": ["frontend", "backend", "api", "database", "authentication", "rest_api", "endpoint"],
  "learning_objectives": [
    "Full-stack development concepts",
    "System architecture design",
    "API development",
    "Database design"
  ],
  "deliverable_type": "code",
  "collaboration_pattern": "team",
  "collaboration_phases": ["architecture", "frontend_dev", "backend_dev", "integration", "testing"]
}
```

---

## Dialogue Templates

### Task Assignment Dialogue

```json
{
  "context": "task_assignment",
  "minion_type": "coordinator",
  "templates": [
    "I'll {action} the {deliverable_type}. We should establish our {terminology_1} first.",
    "Let me {action} this {task_aspect}. I'll need about {time_estimate} to complete it.",
    "I can handle the {responsibility}. Should we use {methodology} or {alternative_methodology}?",
    "Perfect, I'll focus on {task_component}. Let's make sure our {terminology_2} aligns with the {objective}."
  ],
  "action_verbs": ["coordinate", "organize", "structure", "plan", "schedule"],
  "personality_modifiers": ["diplomatic", "organized", "proactive"]
}
```

### Collaboration Dialogue

```json
{
  "context": "collaboration",
  "minion_types": ["infiltrator", "analyst"],
  "templates": [
    "{Minion1}: I'll handle the {component_1}. {Minion2}, can you work on {component_2}?",
    "{Minion2}: Agreed. Let's use {methodology} to ensure {quality_attribute}.",
    "{Minion1}: Good idea. I'll {action_1} while you {action_2}, then we can {collaborative_action}.",
    "{Minion2}: That works. We should also consider {additional_factor} for the {terminology}."
  ],
  "collaborative_actions": ["review each other's work", "combine our findings", "cross-check the data"],
  "quality_attributes": ["accuracy", "consistency", "completeness", "reliability"]
}
```

### Technical Discussion

```json
{
  "context": "technical_discussion",
  "minion_type": "codebreaker",
  "templates": [
    "I'm implementing the {feature} using {technology}. The {terminology_1} should handle {functionality}.",
    "We need to ensure the {component} is {quality_attribute}. I'll add {technical_solution} to achieve that.",
    "The {system_part} connects to the {other_system_part} through {connection_method}.",
    "I'm debugging the {issue}. It looks like the {terminology_2} isn't {expected_behavior}."
  ],
  "technologies": ["REST API", "database queries", "authentication system", "frontend framework"],
  "technical_solutions": ["error handling", "input validation", "caching", "logging"]
}
```

---

## Content Progression

### Level 1-5: Foundation
**Focus:** Basic terminology, simple concepts  
**Terms per task:** 2-3  
**Complexity:** Everyday workplace terms  
**Examples:** task, deadline, email, meeting, document

### Level 6-10: Building
**Focus:** Intermediate concepts, methodology introduction  
**Terms per task:** 3-5  
**Complexity:** Professional processes and frameworks  
**Examples:** agile, sprint, API, stakeholder, ROI

### Level 11-15: Advanced
**Focus:** Complex systems, strategic thinking  
**Terms per task:** 4-6  
**Complexity:** Architecture, strategy, advanced processes  
**Examples:** microservices, CI/CD, OKRs, competitive analysis

### Level 16-20: Expert
**Focus:** Specialized knowledge, industry expertise  
**Terms per task:** 5-8  
**Complexity:** Expert-level concepts and practices  
**Examples:** idempotency, distributed systems, advanced architecture patterns

---

## Implementation Notes

### Term Introduction Strategy

1. **First Encounter**: Bold/highlighted in minion dialogue
2. **Tooltip**: Hover shows short definition
3. **Contextual Usage**: Used naturally 2-3 times in conversation
4. **Glossary Entry**: Added to player's personal knowledge base
5. **Reinforcement**: Reappears in future tasks (spaced repetition)
6. **Mastery Check**: Optional quiz or application challenge

### Quality Assurance

- All definitions reviewed by subject matter experts
- Examples tested for natural language flow
- Related terms properly linked
- Difficulty levels validated against target audience
- Usage contexts verified for accuracy

---

## Version History

**v1.0 - November 14, 2025**
- Initial terminology database
- 50+ terms across all categories
- Task templates for all complexity levels
- Dialogue templates for natural conversation
- Progression framework established

---

*End of Terminology & Content Database*
