# **Role of a System Analyst**

A **System Analyst** sits right in the middle of the whole software development process.  
They act as the **bridge** between the users who need the system and the technical team that will build it.

Their job ain’t just writing documents — they’re the ones who **understand the business problem, translate it into technical language, and guide the project** so the final software actually solves the real issues.  
They work with people, processes, data, and technology all at the same time.

## **Understanding the Work of a System Analyst**

A system analyst’s role is built on one core idea:  
**“Understand what the system should do, why it should do it, and how it should fit into the organization.”**

They don’t code the system themselves—but without them, developers would be guessing instead of building what’s really needed.

## **Key Responsibilities of a System Analyst**

### **1. Requirement Gathering & Understanding**

The most important role.  
They work with:

- Users
- Managers
- Stakeholders

to uncover the **true requirements**, not just what people say on the surface.  
They use interviews, observation, questionnaires, and workshops to understand:

- What the current system does
- Where it fails
- What the new system must fix
- What constraints exist

They turn vague ideas into **clear, structured requirements**.

### **2. Problem Analysis**

Once requirements are gathered, the analyst studies:

- Current workflows
- Data flow
- Pain points
- Bottlenecks
- Inefficiencies

Their goal is to **identify the root problem**, not just the symptoms.  
They decide whether the new system needs:

- Automation
- Simplification
- Integration
- Completely new processes

They basically diagnose before prescribing a solution.

### **3. Feasibility Study**

A system analyst evaluates whether the project is actually possible.

They study:

- **Technical feasibility** → Is the technology available?
- **Operational feasibility** → Will users accept and use it?
- **Economic feasibility** → Is the project cost-effective?
- **Legal feasibility** → Any legal constraints?
- **Schedule feasibility** → Can it be completed in time?

This ensures the team doesn’t start something impossible or unprofitable.

### **4. System Design Support**

Analysts guide the design of:

- Input/output structure
- Data models
- Process models
- Interface structures
- Architecture guidelines

They don’t build the architecture themselves, but they **shape the design** by defining what the system must achieve and how the pieces should fit together.

### **5. Communication Link Between Users and Developers**

This is where they shine the most.  
Users don’t talk in technical terms, and developers don’t speak business language.  
So the analyst:

- Translates **user needs → technical specifications**
- Translates **technical issues → user-friendly explanations**

This avoids misunderstandings, reduces rework, and keeps both sides aligned.

### **6. Documentation**

A system analyst prepares all key documents, such as:

- SRS (Software Requirements Specification)
- Data flow diagrams
- Use case diagrams
- Functional requirements
- Non-functional requirements
- User stories

These documents are the **foundation** for design and development.

### **7. Coordination During Development**

Even after requirements are finalized, the analyst stays involved.  
They:

- Clarify doubts for developers
    
- Handle requirement changes
    
- Ensure the design matches business needs
    
- Keep users updated
    

They make sure the project doesn’t drift off-track.

### **8. System Testing Participation**

They help define:
- Test cases
- Acceptance criteria
- Validation steps

Since they know exactly how the system should behave, they guide the testing team to check whether the system meets the original requirements.

### **9. User Training and Support**

Before the system goes live, the analyst:

- Trains users
- Prepares user manuals
- Demonstrates new workflows
- Ensures users are comfortable with the new system

Their goal is smooth adoption.

### **10. Change Management**

If the system or requirements shift later, the analyst manages:

- Impact analysis
- Updated requirements
- Documentation updates
- Communication with stakeholders

They maintain the continuity of the project.

## **Skills Required for a System Analyst**

A good analyst needs:

- Strong communication
- Analytical thinking
- Understanding of business processes
- Basic technical knowledge
- Modeling skills
- Problem-solving ability

--- 
# **Functional and Non-Functional Requirements**

When a new software system is planned, the very first thing that must be understood clearly is **what the system should do** and **how the system should behave**.  
These expectations are captured as **requirements**, and every requirement fits into one of two categories:  
**Functional** or **Non-functional**.

Functional requirements describe the **actions** the system must perform.  
Non-functional requirements describe the **quality** and **standards** the system must maintain.

Both are equally important—one defines _what_ the system delivers, the other defines _how well_ it delivers it.

# **Functional Requirements**

Functional requirements are the **features, behaviors, and operations** the system must be able to perform.  
They define **what the system should do** from a user and system perspective.

They specify:

- Inputs the system must accept
- Outputs the system must produce
- Processes and workflows the system must follow
- Data handling rules
- Specific actions triggered by certain conditions

In short, these requirements describe the **core functionality** of the software.

## **Characteristics of Functional Requirements**

Functional requirements are:

- **Specific and descriptive**
- **Directly related to user tasks**
- **Testable** (you can check if the system performs the function)
- **Essential for system behavior**

They act like the blueprint for developers to build actual features.

## **Examples**

- A login system that verifies username and password
- A banking app that allows transferring money between accounts
- A hospital system that stores and retrieves patient records
- An e-commerce site that processes orders and payments
- A college portal that generates grade reports

All these describe **actions** or **operations** of the system.

## **Why Functional Requirements Matter**

They ensure:

- Developers know exactly what to build
- Testers know what scenarios to verify
- The system fulfills the users’ tasks
- The business goals are met through features

If functional requirements are unclear, the entire project risks failure.

# **Non-Functional Requirements**

Non-functional requirements (NFRs) describe the **quality attributes**, **constraints**, and **conditions** under which the system must operate.  
They do _not_ define actions or features; instead, they define the **standards** and **performance expectations**.

They answer questions like:

- How fast should it work?
- How secure must it be?
- How reliable must it remain?
- How easy should it be for users to learn?

These qualities shape the _user experience_, _system stability_, and _overall performance_.

## **Characteristics of Non-Functional Requirements**

NFRs are:

- **Qualitative**, not action-oriented
- **Measurable** (good NFRs have metrics)
- **Crucial for user satisfaction**
- **Essential for system reliability and performance**

Functional requirements may get the system running, but NFRs make it **usable and trustworthy**.

## **Major Types of Non-Functional Requirements**

### **1. Performance Requirements**

Define speed, response time, throughput, and efficiency.  
Example: The system must load the dashboard within **3 seconds**.

### **2. Reliability Requirements**

Describe the system’s ability to operate without failures.  
Example: Server uptime must be **99.9%**.

### **3. Security Requirements**

Define protection against unauthorized access and attacks.  
Example: Passwords must be stored using encryption.

### **4. Usability Requirements**

Define how easy it should be for users to learn and use the system.  
Example: New users should understand the interface within **10 minutes**.

### **5. Maintainability Requirements**

Specify how easily developers can fix issues or update the system.  
Example: Code should follow standard naming conventions.

### **6. Scalability Requirements**

Define how well the system can grow under increased load.  
Example: Must support up to **10,000 concurrent users**.

### **7. Portability Requirements**

Specify the ability to run on different environments.  
Example: The software must run on Windows, macOS, and Linux.

### **8. Compatibility Requirements**

Define how well the system interacts with other systems.  
Example: Must integrate with existing billing software.

## **Examples**

- “System should respond to a search query within 2 seconds.”
- “User data must be encrypted using AES-256.”
- “Application must run on both Android and iOS.”
- “System must support 1,000 new user registrations per hour.”

These tell you **how well** the system must perform.

---
# **Difference Between Functional and Non-Functional Requirements**

| Aspect      | Functional Requirements       | Non-Functional Requirements                    |
| ----------- | ----------------------------- | ---------------------------------------------- |
| **Focus**   | What the system should do     | How the system should behave                   |
| **Type**    | Actions, operations, features | Quality attributes, constraints                |
| **Nature**  | Descriptive, task-based       | Performance or quality-based                   |
| **Testing** | Functional testing            | Performance, security, usability testing       |
| **Example** | “User can reset password.”    | “Password reset must occur within 30 seconds.” |
# **Importance of Both Requirement Types**

Both requirement categories are essential because:

- Without functional requirements → the system can’t perform tasks
- Without non-functional requirements → the system becomes slow, insecure, or frustrating to use

Good software balances **capability** (functional) and **quality** (non-functional).

--- 
# **The Software Requirements Document (SRS)**

A _Software Requirements Document_—commonly known as the **Software Requirements Specification (SRS)**—is the formal, structured, and authoritative description of what a software system must do and the conditions under which it must operate. It acts as a **contract** between the client and the development team, ensuring everyone shares the same understanding before design and coding begin.

It is not just a list of requirements; it is a **carefully organized technical document** that captures the _purpose, scope, features, constraints, performance expectations,_ and _external interactions_ of the software. Because it is usually the earliest artifact in the SDLC, its clarity and completeness deeply influence the success of the entire project.

## **Purpose of an SRS**

### **1. Communication Tool**

The SRS translates abstract user needs into precise, testable engineering terms. Clients, system analysts, developers, testers, and managers all rely on this document to stay aligned.

### **2. Foundation for Design and Development**

The SRS defines the “_what_” of the system. Designers use it to derive system architecture and components.

### **3. Basis for Testing**

Testers derive **test cases** directly from functional and non-functional requirements. A clear SRS ensures accurate and objective testing.

### **4. Legal Agreement**

The SRS minimizes misunderstandings by documenting every requirement explicitly, serving as a binding reference when disputes arise regarding what was or wasn’t included.

### **5. Project Management Reference**

Effort estimation, scheduling, budgeting, and resource allocation depend heavily on the scope and clarity of the SRS.

## **Characteristics of a Good SRS**

To be effective, an SRS must possess certain qualities:

### **1. Correct**

Every requirement must match the client’s actual needs.

### **2. Complete**

All possible inputs, outputs, functions, constraints, and system behaviors must be thoroughly documented.

### **3. Unambiguous**

Requirements should have one clear meaning, avoiding vague terms like “fast,” “user-friendly,” or “efficient.”

### **4. Verifiable**

Every requirement should be testable. If it cannot be checked through testing, inspection, or analysis, it isn’t verifiable.

### **5. Consistent**

Requirements must not contradict each other in logic, terminology, or constraints.

### **6. Traceable**

Each requirement should have a unique identifier so that it can be linked back to its origin and traced forward into design, coding, and testing.

### **7. Modifiable**

The document should be structured in a way that makes updates easy and safe without causing ambiguity.

### **8. Feasible**

Requirements should be realistic within the organization’s technology, time, and resource constraints.

## **Structure of a Typical SRS Document**

A standard SRS follows a recognized structure (for example, IEEE 830 guidelines). The major sections often include:

### **1. Introduction**

- Purpose of the system
- Scope of the product
- Definitions, acronyms, and abbreviations
- References used
- Overview of the document

### **2. Overall Description**

- Product perspective
- Product functions
- User characteristics
- Constraints (technical, regulatory, hardware)
- Assumptions and dependencies

### **3. Specific Requirements**

This is the most important and longest section.

#### **a. Functional Requirements**

Detailed descriptions of system functions, inputs, outputs, workflows, and behaviors.

#### **b. Non-functional Requirements**

Covers:

- Performance
- Security
- Reliability
- Usability
- Portability
- Maintainability

#### **c. External Interface Requirements**

- User interfaces
- Hardware interfaces
- Software interfaces
- Communication interfaces

### **4. Other Requirements**

Sometimes includes:

- Database requirements
- Safety requirements
- Standards compliance
- Legal or regulatory constraints

### **5. Appendices**

Supporting information or diagrams:

- Data dictionaries
- Use-case diagrams
- Glossary

--- 
# **Introduction to Software Design**

Software design is the **transformation of requirements** (captured in the SRS) into a **structured blueprint** for building the software system. It is the stage where vague problem statements evolve into clear, organized, and technically sound solutions. While requirement analysis tells us _what_ the system must do, software design determines _how_ the system will achieve it.

It is an intellectual, creative, and systematic activity where developers and designers make decisions about system architecture, data structures, interfaces, algorithms, and component interactions. The quality of this stage strongly influences the quality, performance, maintainability, and adaptability of the final product.

## **Purpose of Software Design**

### **1. Bridge Between Requirements and Implementation**

Design acts as the middle layer between problem understanding and coding. It converts user needs into actionable structures that developers can implement.

### **2. Provide a Blueprint for Construction**

Just like architectural plans for a building, software design provides diagrams, models, and specifications that guide coding, integration, and testing.

### **3. Reduce Complexity**

Complex systems are broken into smaller, manageable subsystems and modules that are easier to understand, design, code, and test.

### **4. Improve Maintainability and Scalability**

Good design anticipates future changes. A well-designed system is easier to modify, extend, or adapt as requirements evolve.

### **5. Ensure Reliability and Efficiency**

Design choices affect performance, fault tolerance, and system robustness. Early decisions help prevent costly errors later.

## **Nature of Software Design**

Software design is both **systematic** and **creative**:
### **1. Systematic**

It follows clear principles, patterns, and guidelines to make decisions methodically, avoiding ad-hoc development.

### **2. Creative**

It requires problem-solving, innovation, and judgment to choose the best architecture or data structures for specific contexts.

## **Levels of Software Design**

Software design is not done in one step. It unfolds in two major levels:

### **1. High-Level Design (HLD) — Architectural Design**

This phase determines the **overall structure** of the system.

#### **Key Focus Areas**

- System architecture
- Major modules/subsystems
- Data flow among modules
- Technology stack decisions
- External interfaces
- High-level database structure

#### **Outputs**

- Architecture diagrams
- Data Flow Diagrams (DFDs)
- System block diagrams
- Interface descriptions

HLD answers:  
**“What are the major components and how do they interact?”**

### **2. Low-Level Design (LLD) — Detailed Design**

This phase dives deep into the **internal workings** of each module.

#### **Key Focus Areas**

- Data structures
- Algorithms
- Function/class definitions
- Pseudocode
- Error handling
- Database table details
- Interface design

#### **Outputs**

- Class diagrams
- Sequence diagrams
- State diagrams
- Pseudocode for critical functions

LLD answers:  
**“How will each component be implemented in code?”**

## **Activities in Software Design**

### **1. Architectural Design**

Choosing architecture style (layered, client-server, microservices, etc.)

### **2. Interface Design**

Defining how modules interact with each other and with users.

### **3. Component Design**

Identifying components, their responsibilities, and communication methods.

### **4. Data Design**

Selecting data structures, organizing databases, defining schemas and data flow.

### **5. Algorithm Design**

Establishing logic and control flow for processing data.

## **Characteristics of Good Software Design**

A well-prepared design exhibits the following qualities:
### **1. Correctness**

It must satisfy all requirements from the SRS.

### **2. Efficiency**

Optimizes resource usage—CPU, memory, bandwidth.

### **3. Modularity**

Divides system into independent, reusable units.

### **4. Understandability**

Easy for new developers to read, analyze, and extend.

### **5. Maintainability**

Supports fixing issues, adding features, or modifying behavior easily.

### **6. Reusability**

Encourages using components in multiple systems.

### **7. Reliability**

Design must support fault handling and consistent performance.

### **8. Flexibility**

Design should allow future enhancements without drastic changes.

## **Why Software Design is Essential**

### **1. Reduces Development Cost**

Errors caught early in design save time and money.

### **2. Improves Software Quality**

Good design directly contributes to fewer bugs, better performance, and stronger security.

### **3. Simplifies Teamwork**

Clear design makes it possible for large teams to work in parallel.

### **4. Provides Roadmap for Future Maintenance**

Since most project costs arise during maintenance, good design reduces long-term effort.

--- 
# **Preliminary Design Phase and Detailed Design Phase**

In the software design process, work unfolds in **two major phases**: the _Preliminary Design Phase_ and the _Detailed Design Phase_. Together, they convert the high-level requirements from the SRS into a complete, implementable blueprint. These phases should always be seen as consecutive layers—first shaping the system’s big picture, then refining every small internal element.

# **Preliminary Design Phase (High-Level / Architectural Design)**

## **Purpose**

The preliminary design phase focuses on defining the **overall structure and architecture** of the system. This is where the development team steps back to look at the system as a whole and decides _how major pieces of the product will fit together_. It aims to break the system into manageable components and identify how these components interact.

This phase answers the question:  
**“How will the system be organized at the macro level?”**

## **Key Activities**

### **1. Architectural Style Selection**

Choosing the architecture pattern that suits the system’s needs, such as:

- Layered architecture
- Client–server
- Microservices
- Data-centered architecture
- Pipes-and-filters

Each style gives a different shape to how components communicate and how data flows.

### **2. System Decomposition**

Breaking the system into **subsystems, major modules, and components**.  
This step reduces complexity by dividing the system into meaningful, independent functional blocks.

### **3. Identification of Interfaces**

Determining how:

- Modules interact
- Users interact with the system
- External devices or systems connect

### **4. Data Design at a High Level**

Outlining:

- Major data objects
- High-level database structure
- Data flow across the system

### **5. Establishing System Constraints**

Accounting for:

- Hardware limitations
- Software platforms
- Security and regulatory constraints
- Performance expectations

## **Outputs of the Preliminary Design Phase**

### **1. System Architecture Diagram**

A visual overview showing major components and their relationships.

### **2. High-Level Data Flow Diagrams**

Illustrates how data moves through the system.

### **3. Interface Descriptions**

Defines how components connect and communicate.

### **4. Technology Decisions**

Frameworks, programming languages, libraries, and external services chosen early.

## **Importance of the Preliminary Design Phase**

- Provides the system’s _structural backbone_.
- Ensures alignment between developers, managers, and stakeholders.
- Reduces risk by clarifying the major design decisions upfront.
- Makes sure the design matches the constraints specified in the SRS.

# **Detailed Design Phase (Low-Level Design)**

## **Purpose**

The detailed design phase builds on the preliminary design by diving deep into **each module’s internal structure and behavior**. This phase elaborates how every component will operate at the code level.

It answers:  
**“How will each component be implemented internally?”**

## **Key Activities**

### **1. Data Structure Design**

Defining:

- Specific variables
- Data types
- Composite structures
- Classes and objects

These details directly guide implementation.

### **2. Algorithm Design**

Outlining:

- Logical steps
- Control flow
- Error handling
- Optimized algorithm choices

This often includes pseudocode or flowcharts.

### **3. Component-Level Interface Specification**

Documenting:

- Function signatures
- Input and output formats
- Parameter constraints
- Error codes or exceptions

### **4. State Modeling**

Using diagrams like:

- State transition diagrams
- Sequence diagrams
- Activity diagrams

These capture how internal components react to events.

### **5. Database Table-Level Design**

Specifying:

- Detailed schema
- Relationships
- Primary/foreign keys
- Normalization considerations

### **6. Internal Logic of Modules**

Every module gets a precise low-level description so any developer can implement it consistently.

## **Outputs of the Detailed Design Phase**

### **1. Class Diagrams**

Shows structure, attributes, methods, and relationships.

### **2. Sequence Diagrams**

Shows how objects collaborate during operations.

### **3. Pseudocode**

Provides a step-by-step guide to coding functions or modules.

### **4. Detailed Database Schema**

Shows tables, fields, keys, and constraints.

### **5. Module Specifications**

A document describing each component precisely so coding becomes straightforward.

## **Importance of the Detailed Design Phase**

- Eliminates ambiguity before coding begins.
- Helps developers write efficient and consistent code.
- Reduces bugs caused by unclear logic.
- Provides a reference document for future maintenance.
- Makes the transition from design to coding smooth and structured.

# **Relationship Between the Two Phases**

## **Preliminary Design Phase**

- Big-picture vision
- Architectural planning
- Focuses on _what modules exist_ and _how they interact_

## **Detailed Design Phase**

- Micro-level planning
- Internal component logic
- Focuses on _how each module works internally_

Together, they ensure the system is both **well-structured at the top level** and **well-defined at the implementation level**.

--- 
# Terms in Modern Software Design 
# **Cohesion 

Cohesion is one of the most important ideas in software design. At its core, cohesion describes **how tightly the responsibilities inside a single module belong together**. When a module focuses on one clear purpose and all its internal parts support that purpose, we say it has **high cohesion**.

High cohesion is considered a sign of **clean, professional, and maintainable** design. Low cohesion, on the other hand, usually signals a messy module doing too many unrelated things — which makes the system harder to understand, modify, or debug.

## **What Cohesion Really Means**

Cohesion measures the **strength of internal relationships** within a module.  
A module with high cohesion:

- Handles _one job_ or one well-defined set of related tasks.
- Has pieces that depend on each other naturally.
- Feels organized and meaningful — you can read it and instantly understand what it's for.

A module with low cohesion:

- Tries to do many unrelated things.
- Holds logic that doesn’t naturally belong together.
- Feels scattered, confusing, and fragile.

In simple terms:  
**High cohesion = focused module.**  
**Low cohesion = confused module.**

## **Why Cohesion Matters**

### **1. Makes Code Easy to Understand**

When a module has one clear purpose, new developers can grasp it quickly. The mental effort drops, and learning the system becomes easier.

### **2. Improves Maintainability**

Any future change becomes more predictable. Fixing or updating one cohesive module rarely breaks others, because responsibilities aren’t mixed up.

### **3. Encourages Reusability**

A cohesive module performs a single well-shaped task. That makes it easy to reuse the module elsewhere without unwanted side effects.

### **4. Reduces Errors and Side Effects**

Modules with multiple scattered responsibilities often cause bugs when one part gets modified. Cohesion keeps behavior contained and stable.

### **5. Supports Good Architecture**

Modern design approaches — object-oriented design, microservices, modular architectures — all rely on cohesion to keep components clean and independent.

## **Types of Cohesion (from weakest to strongest)**

Even though exam answers don’t need full implementation examples, you _do_ need to know the classic categories of cohesion and how they differ. These categories show the spectrum from poor to excellent design.

### **1. Coincidental Cohesion (Worst)**

- Elements inside the module have no meaningful relationship.
- Grouped together “just because.”

### **2. Logical Cohesion**

- Functions grouped because they fall in the same general category.
- The module chooses behavior based on a control flag (bad practice).

### **3. Temporal Cohesion**

- Elements executed around the same time (e.g., startup tasks).
- Related by timing, not by purpose.

### **4. Procedural Cohesion**

- Elements grouped because they follow a specific sequence.
- Still doesn’t ensure they’re conceptually related.

### **5. Communicational Cohesion**

- Elements operate on the same dataset.
- Stronger, but still might bundle unrelated logic.

### **6. Sequential Cohesion**

- Output of one function becomes input for another inside the same module.
- Shows clear logical flow.

### **7. Functional Cohesion (Best)**

- Every element works toward **one single function or purpose**.
- The module is clean, sharp, and focused.

## **Cohesion in Modern Design Approaches**

### **Object-Oriented Design**

A class must represent **one clear responsibility**. This is also known as the _Single Responsibility Principle (SRP)_, which directly expresses the idea of cohesion.

### **Component-Based Design**

Components serve specific business capabilities. High cohesion ensures:

- Clear boundaries
- Better testability
- Reduced coupling between services

### **Microservices Architecture**

Each microservice should handle **one specific business function**. If a microservice tries to do too much, cohesion breaks — leading to bloated, unstable services.

## **Signs of High Cohesion**

- Module name clearly reflects its purpose
- All functions feel naturally connected
- Removing or adding a function doesn't break conceptual unity
- No “giant classes” doing everything
## **Signs of Low Cohesion**

- Hard to name the module in one short phrase
- Functions inside feel unrelated
- Frequent ripple effects when modifying logic
- Multiple responsibilities crammed together

--- 
# **Coupling 

If cohesion tells you how tight things are _inside_ a module, **coupling** tells you how much one module **depends on another**.

In simple terms:  
**Coupling = the degree of interdependence between modules.**

High coupling means modules can’t live without each other — they tangled up and fragile.  
Low coupling means modules mind their own business, talk only when necessary, and stay independent.

Modern software design always aims for **low coupling**, ‘cause that’s what keeps systems flexible, easy to maintain, and resistant to breaking when something changes.

# **What Coupling Really Means**

Coupling looks at how many connections two modules share — data, control signals, structures, or internal details.

### **Low Coupling (Good)**

- Modules communicate only using well-defined interfaces.
- One module can change without forcing the whole system to change.
- The system becomes modular, testable, and cleaner.

### **High Coupling (Bad)**

- Modules depend heavily on each other’s behavior.
- If one module changes, others break.
- Hard to test, debug, or update.
- System feels rigid and tangled.

# **Why Coupling Matters**

### **1. Makes Maintenance Easier**

If modules don’t depend on internal details of each other, you can change one without rewriting five more.

### **2. Enhances Reusability**

Low-coupled modules are more reusable ‘cause they don’t drag a bunch of other code with them.

### **3. Improves Testability**

A loosely coupled module can be tested independently, without needing the whole system running.

### **4. Supports Scalability**

Systems with low coupling can grow, split, or evolve without creating chaos.

### **5. Reduces Risk**

Design changes stay controlled — no “fix one bug, create three more” situation.

# **Types of Coupling (from worst to best)**

## **1. Content Coupling (Worst)**

- One module directly modifies or depends on the internal workings of another.
- Example: accessing internal variables or jumping into another module’s code.
- Extremely fragile.

## **2. Common Coupling**

- Multiple modules share the same global data.
- Any change affects every module using it.

## **3. External Coupling**

- Modules depend on externally imposed data formats or communication protocols.
- Changes in external specifications force code changes.

## **4. Control Coupling**

- One module controls another’s behavior by passing control information (flags or commands).
- Still manageable but not ideal.

## **5. Stamp Coupling (Data-structure Coupling)**

- Modules share a data structure, even if they only need part of it.
- Unnecessary dependence on entire structures.

## **6. Data Coupling (Best Practical Level)**

- Modules interact by passing only the data needed.
- Clean, modular, and stable.

## **7. No Coupling (Ideal but Not Realistic)**

- Modules are completely independent.
- Rare in real projects because modules must collaborate somehow.

# **Coupling in Modern Design Approaches**

## **Object-Oriented Programming**

Low coupling is encouraged through:

- Encapsulation
- Interfaces
- Access modifiers
- Design principles like SOLID

Especially **DIP (Dependency Inversion Principle)** — depend on abstractions, not concrete classes.

## **Component-Based Design**

Components should communicate via well-defined APIs.  
Low coupling keeps each component independent and replaceable.

## **Microservices Architecture**

Each service should function as its own independent unit.  
Low coupling ensures:

- Services can be deployed separately
- Teams can work independently
- Failures don’t cascade across the system

Coupling usually happens through lightweight communication (REST APIs, event queues).

# **Signs of Low Coupling**

- Modules talk through interfaces, not internal details
- Dependencies are clear and minimal
- Changing one module rarely breaks others
- System feels flexible and modular
# **Signs of High Coupling**

- Modules share global variables
- One module knows too much about another’s internals
- Frequent ripple effects when making changes
- Hard to isolate modules during testing

# **Relationship Between Cohesion and Coupling**

These two always work together:

- **High cohesion + Low coupling** = best possible design
- **Low cohesion + High coupling** = messy, unstable system

Together, they decide how clean, maintainable, and understandable your architecture is.

--- 
# **Functional Independence**

Aight, let’s lay this out smooth.  
**Functional independence** is one of the core goals of modern software design. It means each module in the system handles **one well-defined function** and does it without leaning too hard on other modules.

It’s basically the _ideal combo_ of:

- **High cohesion** (module stays focused internally)
- **Low coupling** (module avoids unnecessary dependence externally)

When a system reaches functional independence, every part feels clean, organized, and easy to grow — just like a well-run team where everyone handles their lane without stepping on each other’s toes.

# **Meaning of Functional Independence**

Functional independence means:
### **1. Each module performs one specific function**

Every module is designed with a single, clear purpose and all its internal pieces support that purpose.

### **2. Modules don’t depend heavily on each other**

They interact through simple, well-defined interfaces instead of sharing internal data or complicated control signals.

### **3. Changes to one module don’t mess up others**

Because modules don’t depend on each other's internal logic, updating one doesn’t create a cascade of issues.

In short:  
**A module does its job fully, clearly, and without depending on the inner life of other modules.**


# **Use o fFunctional Independence 

## **1. Easier to Understand**

When each module does only one thing and does it clearly, developers can grasp its purpose instantly.

## **2. Easier to Maintain**

If something breaks or needs updating, you only touch the module responsible for that function — no side effects elsewhere.

## **3. Easier to Test**

Independent modules can be tested in isolation.  
Unit testing becomes clean and reliable.

## **4. Encourages Reusability**

A functionally independent module becomes a reusable building block because it doesn’t drag along external dependencies.

## **5. Enhances Reliability**

Fewer cross-connections = fewer hidden bugs and fewer chain-reaction failures.

# **Functional Independence = Cohesion + Coupling**

Functional independence is directly tied to the two design attributes you just learned:

## **High Cohesion**

- All activities inside a module contribute to the same task.
- The module has one focused purpose.
- Best form: _Functional cohesion_.

## **Low Coupling**

- Modules interact only when they need to.
- Communication stays simple and interface-based.
- Internal details stay hidden.

**When you combine high cohesion with low coupling, you achieve functional independence.**

# **Characteristics of a Functionally Independent Module**

- Has a single, clear responsibility
- Implements that responsibility completely
- Contains all logic related to its function internally
- Offers a small, clean interface
- Doesn’t rely on global variables
- Doesn’t require knowledge of other modules’ internal structures

# **Functional Independence in Modern Design Approaches**

## **1. Object-Oriented Design**

Design principles like the _Single Responsibility Principle (SRP)_ and _Encapsulation_ support functional independence.

## **2. Component-Based Systems**

Each component represents a self-contained service or capability.

## **3. Microservices Architecture**

Each microservice is responsible for exactly one business function — the highest practical level of functional independence.

## **4. Modular Monoliths**

Even in monolithic systems, functional independence helps divide the codebase into stable, separate modules.

# **Benefits for the SDLC**

- More predictable design
- Easier debugging
- Faster implementation
- Smooth testing and integration
- Cleaner long-term maintenance and updates

--- 
# **Topic: Top-down and Bottom-up Approaches for Software Design**

### **Top-Down Design Approach**

- This approach start from the **big picture** and then break it down step-by-step.
- You begin with the **overall system** → divide it into **major modules** → break those modules into **sub-modules**, and so on.
- It’s basically: _“Start from the top, then drill down.”_

#### **Key Points**

- Focus on **overall functionality** first.
- Easy to **understand** and **organize** early on.
- Good for projects where **requirements are clear**.
- Design is structured like a **hierarchy**.
- Testing follows a **top-down integration**: start with higher modules, add lower ones later.

### **Bottom-Up Design Approach**

- This one starts from the **smallest components** first.
- Build **independent modules**, utilities, reusable components → then combine them to form the **complete system**.
- It’s basically: _“Start from the small pieces, then assemble ‘em.”_

#### **Key Points**

- Focus on **reusable components** first.
- Good when the lower-level details or utilities are already known.
- Helps in building **robust, reusable code libraries**.
- Testing follows **bottom-up integration**: start testing small modules first, then combine.

### **Difference (Simple)**

| Point           | Top-Down           | Bottom-Up           |
| --------------- | ------------------ | ------------------- |
| Start Point     | System-level       | Component-level     |
| Flow            | Break big → small  | Combine small → big |
| Best For        | Clear requirements | Reusable modules    |
| Integration<br> | High → low         | Low → high          |
### **Where They Used**

- **Top-down:** traditional apps, procedural systems, systems with stable requirements.
- **Bottom-up:** object-oriented design, library building, utility-heavy systems.

--- 
# Introduction to Data Flow Diagram (DFD)

- A **Data Flow Diagram (DFD)** show how **data moves** inside a system.

- It don’t focus on _how_ things happen internally — only **what data flows where**, **who sends it**, **who receives it**, and **what processes transform it**.
- It’s used heavy during **requirement analysis** to understand the system clearly.

### **Why DFDs Are Used**

- To give a **visual picture** of the system.
- Helps analyst, users, and developers get on the **same page**.
- Makes it easier to spot **missing, unclear, or redundant** requirements.
- Works as a **bridge** between users and designers.

### **DFD Components (Symbols)**

These four symbols always show up:

1. **Process**
    
    - Shows some operation or transformation on data.
    - Notation: Circle or rounded rectangle.
       
2. **Data Flow**
    
    - The movement of data from one place to another.
    - Notation: Arrow.
	
3. **Data Store**
    
    - Where data gets kept / saved.
    - Notation: Open-ended rectangle (looks like `||----`).
	
4. **External Entity (Terminator)**
    
    - People, devices, or other systems **outside** your system that send or receive data.
    - Notation: Rectangle.

### **Levels of DFD**

DFDs come in _layers_, from general → detailed:

1. **Context Diagram (Level 0 DFD)**
    
    - Shows the **whole system as one big process**.
    - Only includes: system, external entities, and data flows.
    - No data stores here.
	
2. **Level 1 DFD**
    
    - Breaks the main process into **major sub-processes**.
    - Includes data stores.
	
3. **Level 2 (and more)**
    
    - Breaks each Level-1 process into **smaller and more detailed** processes.

### **Rules / Guidelines**

- Every process must have **at least one input and one output**.
- Data must flow **through a process** — it can’t go directly entity → entity or store → store.
- Parent and child diagrams must be **balanced** (same inputs/outputs).
- DFDs stay **logical**, not physical — no hardware details.

### **Advantages**

- Simple, easy-to-understand diagrams.
- Useful for finding **bottlenecks** or **missing steps**.
- Works great during **requirement gathering**.
- Helps both technical and non-technical people understand the system.
 --- 
# Use of DFDs for a Good Software Design


DFDs ain’t just drawings — they help lay the **foundation** for a solid, well-structured design. Here’s how:

### **1. Clarifies System Requirements**

- DFDs break the system into **clear processes, data stores, and flows**.
- This reduces confusion and ensures the team understands **exactly what the system must do**.
- Misunderstood requirements get caught early.

### **2. Makes the System Structure Easier to Understand**

- A visual map helps both developers and non-technical users grasp the system quickly.
- Designers can see how everything fits together **before** writing code.

### **3. Supports Logical, Not Physical Design**

- DFDs show the **logic** of data movement, not the technical implementation.
- That makes it easier to design the system **independent of technology choices**.

### **4. Helps Identify Redundancies & Missing Processes**

- If data flows look odd or incomplete, the diagram exposes:
    
    - Missing steps
    - Unnecessary operations
    - Repeated tasks
	
- This leads to cleaner, more efficient designs.
### **5. Guides Modular Design**

- Each process can be turned into a **module** or **function** in the final system.
- Designers can divide the system into **manageable, independent parts**, improving maintainability.

### **6. Ensures Balanced and Consistent Design**

- Since every level of DFD must stay balanced, it forces the design to be:
    
    - **Consistent**
    - **Organized**
    - **Accurate**
	
- No sudden new inputs/outputs appear magically during design.

### **7. Acts as a Blueprint for Developers**

- Once the DFD is ready, developers can use it as a **roadmap** for coding each module.
- It also helps testers understand what to validate.

### **8. Supports Communication Among Stakeholders**

- Users, analysts, designers, and developers can all understand DFDs.
- This leads to fewer misunderstandings and smoother development.


> DFDs improve software design by making it **clear, structured, modular, consistent, and easy to understand**, reducing errors and strengthening the quality of the final product.


---- 
# Structure Charts 

A structure chart is a **graphical, hierarchical diagram** that shows how a system’s modules are organized and how they interact.  
Think of it like the “family tree” of a software system — the **main module sits on top**, and all the submodules branch down below it.

It is used heavily in **structured design** to break a system into **small, independent, and clearly defined modules**.

## **Purpose of a Structure Chart**

A structure chart helps designers understand:

- **How the system is divided into modules**
- **How modules depend on each other**
- **What kind of data or control signals pass between modules**
- **Which parts of the system can be developed or tested independently**

It brings clarity and discipline to the design process by enforcing modular thinking.

## **Key Features of Structure Charts**

### **1. Hierarchical Structure**

- Top-level module at the very top
- Submodules below it
- Each module broken further until functions are small and manageable
- Shows “who calls whom”

### **2. Modules Represented as Boxes**

- Each box = one module
- Modules normally perform **one specific function**

### **3. Arrows Represent Communication**

There are two types:

- **Data flow** (actual data values passed)
- **Control flow** (commands or signals indicating an action)

These arrows make module interaction **explicit**, not hidden.

### **4. Shows Module Relationships**

Structure charts highlight:

- **Superordinate modules** (parents)
- **Subordinate modules** (children)
- **Sibling modules** (same level)
- **Coupling strength** (via how much data they exchange)


## **Importance of Structure Charts 

### **1. Supports Modular Design**

Breaking the system into modules leads to:

- Less complexity
- Easier debugging
- Reduced development time

### **2. Improves Maintainability**

A well-structured chart lets future developers quickly understand:

- Where a function lives
- Which modules rely on it
- How to modify without breaking the system

### **3. Prepares the System for Coding**

Coders get a clear picture of:

- What functions they must implement
- How functions call each other
- What parameters they need

It’s almost like giving them a **blueprint for coding**.

### **4. Helps Detect Weak Design Early**

If a module:

- Does too many tasks
- Depends on too much data
- Has unclear inputs/outputs

…the structure chart exposes that immediately, letting designers fix the structure before implementation.

---

## **Difference Between Structure Charts & DFDs (Quick Note)**

| DFD                          | Structure Chart              |
| ---------------------------- | ---------------------------- |
| Shows _data movement_        | Shows _module hierarchy_     |
| Logical view                 | Design view                  |
| Focus: “What system does”    | Focus: “How system is built” |
| Used in requirement analysis | Used in design phase         |

Both are used together:  
DFDs → define system logic  
Structure charts → convert logic into modular design

--- 
# Example of Structure Chart (ATM System)
### **Top-Level Module**

- **ATM System**  
    This is the main control module. It coordinates all major operations.

## **Breakdown Into Submodules**

The ATM System is divided into four major child modules:

1. **Read Card Module**
2. **Authenticate User Module**
3. **Process Transaction Module**
4. **Print Receipt Module**

These represent the core operations an ATM must perform.

---

## **Further Decomposition of Submodules**

### **1. Read Card Module**

- **1.1 Validate Card**
- **1.2 Read Account Number**

This module handles checking whether the card is usable and fetching the account details.

### **2. Authenticate User Module**

- **2.1 Read PIN**
- **2.2 Verify PIN**

After reading the card, the user has to enter a PIN.  
Verification happens through the bank’s database.

### **3. Process Transaction Module**

This is usually the biggest section, so it gets split like this:

- **3.1 Show Transaction Menu**
- **3.2 Withdraw Cash**
- **3.3 Deposit Cash**
- **3.4 Check Balance**
- **3.5 Transfer Funds**

Each one is its own functional area and can be implemented independently.

### **4. Print Receipt Module**

- **4.1 Prepare Receipt Information**
- **4.2 Print Transaction Receipt**

This module gathers transaction data and prints it on paper.

---

## **What the Structure Chart Looks Like (Textual Form)**

```
                         [ ATM System ]
                     /         |         |        \
            Read Card   Authenticate   Process     Print
              Module      User         Transaction  Receipt
                          Module         Module     Module
             /    \        /   \       /   |   \ 
      Validate  Read   Read  Verify  Menu  Withdraw  Deposit ...
       Card     AccNo   PIN   PIN
```

(You can easily redraw this in the exam using boxes and lines.)

---

## **Why This Example Works Perfectly in Exams**

- Clear hierarchy
- Clean modular breakdown
- Balanced number of submodules
- Easy to explain
- Shows functional independence
- Textual form + visual form structure
