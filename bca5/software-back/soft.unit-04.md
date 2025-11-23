# **Introduction to Software Testing**

Software Testing is the process of **evaluating a software system** to check whether it meets the required specifications and functions correctly.  
In simple terms, testing makes sure the software **does what it’s supposed to do** and **doesn’t break** when users interact with it.

### **Why Software Testing Matters**

- **Catches errors early** before the user sees them.
- **Improves software quality** by ensuring stability, performance, and reliability.
- **Reduces maintenance cost** — fixing early is cheaper than fixing later.
- **Ensures requirement satisfaction** — confirms that the software meets the needs defined in SRS.

### **Goals of Software Testing**

- Find defects and remove them.
- Ensure software behaves correctly in all scenarios.
- Verify that the software meets all functional & non-functional requirements.
- Improve confidence in the product before release.

### **Key Concepts**

**1. Error** – mistakes made by developers.  
**2. Fault/Bug** – incorrect code caused by an error.  
**3. Failure** – when the software behaves unexpectedly because of a bug.

### **Characteristics of Good Testing**

- **Systematic** – follows a planned approach.
- **Repeatable** – can be done again with the same results.
- **Efficient** – finds maximum defects with minimum effort.
- **Independent** – testers should not be the same people who wrote the code (if possible).

### **Types of Testing (Basic Intro)**

Just an overview — you’ll dive deeper in next topics.

1. **Static Testing**
    
    - Done **without executing code** (reviews, inspections, walkthroughs).
	
2. **Dynamic Testing**
    
    - Done **by running the software**.
	
3. **Black Box Testing**
    
    - Focus on **inputs & outputs**, no knowledge of internal code.
	
4. **White Box Testing**
    
    - Tester knows internal logic & structure of code.
	
5. **Integration, System, Acceptance testing**, etc.
    
    - Higher-level testing done before final release.

--- 
# **Test Cases and Test Suites**

## Test Case

A **test case** is a **specific set of steps**, inputs, conditions, and expected results used to check one particular function or behavior of the software.

Basically:  
**“Do this → expect this.”**

### **A Good Test Case Includes**

- **Test Case ID**
- **Objective / Purpose**
- **Pre-conditions** (what must be true before running it)
- **Test Steps** (actions to perform)
- **Input data**
- **Expected Output**
- **Actual Output** (filled after execution)
- **Status** (Pass/Fail)

### **Why Test Cases Matter**

- Ensures testing is **organized, consistent, and repeatable**
- Helps new testers understand what to test
- Provides record of tested functionality
- Useful for regression testing (testing old features after updates)

## ** Test Suite: 

A **test suite** is a **collection of multiple test cases** grouped together based on some purpose.

Think of it like a folder full of test cases that belong to the same module or functionality.

### **Example**

- _Login Module Test Suite_
    
    - Test Case 1: Valid login
    - Test Case 2: Invalid password
    - Test Case 3: Empty form
    - Test Case 4: Forgot password flow
    - Test Case 5: Account lock after 5 failed attempts

### **Why Test Suites Matter**

- Helps organize the testing process module-wise
- Ensures coverage for every part of the system
- Makes automated testing easier
- Useful for running all related tests together

### **Difference Between Test Case & Test Suite**

| Test Case                              | Test Suite                          |
| -------------------------------------- | ----------------------------------- |
| Single scenario                        | Collection of test cases            |
| Focuses on one function                | Focuses on entire module or feature |
| Contains steps, input, expected output | Groups cases without steps          |

--- 
# **Unit Testing**


Unit testing is the process of testing **individual components** or **smallest parts** of a software system — usually functions, methods, or classes — **in isolation** to ensure they work correctly.

It checks:  
**“Is this tiny piece of code doing exactly what it’s supposed to do?”**

### **2. Why Unit Testing is Important**

- Detects bugs **early**, before integration
- Makes debugging easier
- Ensures each part of the system is reliable
- Helps maintain code quality
- Makes future changes safer (supports refactoring)

### **3. Who Performs Unit Testing?**

Usually done by **developers**, not testers.  
Because they understand the internal logic of the code.

### **4. Tools Used for Unit Testing**

- **Java** → JUnit
- **Python** → unittest / pytest
- **C# / .NET** → MSTest, NUnit, xUnit
- **JavaScript** → Jest, Mocha

### **5. Characteristics of Good Unit Tests**

- **Fast** to run
- **Isolated** (no database, no API calls unless mocked)
- **Repeatable**
- **Readable**
- **Automated**

### **6. Example (Simple Idea)**

Testing: `add(a, b)` function

- Input: `2, 3`
- Expected Output: `5`

If it returns anything else, the unit test fails.

--- 
# **Integration Testing**

Integration Testing is the process of testing **how different modules or units of software work together**.  
After each module passes unit testing, integration testing ensures that **interactions between modules** are correct and the combined system works as expected.

Basically:  
**“The pieces work fine individually, but do they play nicely together?”**

### **2. Purpose of Integration Testing**

- Detect errors in **module interfaces** (wrong data passed, incorrect calls)
- Ensure **combined functionality** behaves as required
- Find **interaction defects** missed during unit testing
- Validate **data flow** between modules
- Reduce risk before system-level testing


### **3. Who Performs Integration Testing?**

- Usually **developers** or a **special testing team**
- Can be manual or automated depending on project size

### **4. Types of Integration Testing**

#### **A. Big Bang Integration**

- All modules are integrated at once
- Test the complete system in one go
- **Pros:** Simple to implement
- **Cons:** Hard to identify where errors occur

#### **B. Top-Down Integration**

- Test starts with **high-level modules first**
- Lower-level modules are integrated later
- **Stubs** are used to simulate lower-level modules
- **Pros:** Early testing of main control logic
- **Cons:** Requires stubs, may miss lower-level errors early

#### **C. Bottom-Up Integration**

- Test starts with **low-level modules first**
- Higher-level modules are integrated gradually
- **Drivers** are used to simulate higher-level modules
- **Pros:** Low-level functionality tested early
- **Cons:** Top-level modules tested late

#### **D. Sandwich / Hybrid Integration**

- Combines **top-down** and **bottom-up** approaches
- Middle-level modules tested first
- Efficient for large projects

### **5. Key Concepts in Integration Testing**

- **Module Interface Testing** – ensure correct communication
- **Data Flow Testing** – validate data exchange
- **Incremental Testing** – integrate modules gradually
- **Non-Incremental Testing** – integrate all at once (Big Bang)

### **6. Example Scenario**

Imagine an **online shopping system**:

Modules:

- User Login
- Product Catalog
- Shopping Cart
- Payment Gateway

Integration Test checks:

- Can the **Login module** pass user info to **Shopping Cart**?
- Can **Cart module** send correct order details to **Payment Gateway**?
- Do errors in one module break the workflow?

### **7. Benefits of Integration Testing**

- Detects interface and interaction errors early
- Ensures **system cohesion**
- Reduces errors in later system testing
- Improves reliability and confidence before release

--- 
# **Acceptance Testing**

Acceptance Testing is the **final level of software testing** before the system is delivered to the client or end-user.  
Its main goal is to verify that the **software meets all specified requirements** and is ready for **real-world use**.

Simply:  
**“Does this software do what the customer expects?”**

### **2. Purpose of Acceptance Testing**

- Validate that the system satisfies **business requirements**
- Ensure the software is **ready for deployment**
- Detect issues that were missed in unit, integration, or system testing
- Gain **client confidence** before production release
- Serve as the **final check** against contractual or specification requirements

### **3. Who Performs Acceptance Testing?**

- **End-users or clients** (actual users)
- **QA team** may assist in formalizing tests
- Focus is on **real-world scenarios** rather than internal code logic

### **4. Types of Acceptance Testing**

#### **A. Alpha Testing**

- Done **by internal staff** before releasing the software to customers
- Usually conducted in a **controlled environment**
- Detects **bugs and usability issues** early

#### **B. Beta Testing**

- Done **by actual users** outside the organization
- Software is released to a limited audience
- Feedback is collected for final adjustments

#### **C. Contract Acceptance Testing**

- Based on **contractual requirements**
- Ensures the software fulfills all terms agreed in the contract

#### **D. Regulation Acceptance Testing**

- Checks compliance with **legal, safety, or industry regulations**

#### **E. Operational Acceptance Testing (OAT)**

- Ensures the system is **operationally ready**
- Checks **backup, recovery, performance, and maintenance procedures**

### **5. Key Concepts in Acceptance Testing**

- **Customer-centric**: Focus on user needs and satisfaction
- **Validation-oriented**: Confirms that specifications are correctly implemented
- **Scenario-based**: Often uses real-world business scenarios
- **Non-technical focus**: Users care more about functionality than code

### **6. Example Scenario**

For an **online shopping system**:

- Can a user successfully register and log in?
- Can they search and add products to the cart?
- Does the payment gateway process transactions correctly?
- Are error messages clear and helpful?
- Is the system performance acceptable under normal load?

Feedback from this stage determines whether the software **passes acceptance** or requires changes.

---

### **7. Benefits of Acceptance Testing**

- Ensures software meets **user expectations**
- Reduces risk of post-release issues
- Improves **customer satisfaction and confidence**
- Helps uncover usability or business-process errors missed in earlier testing
- Provides formal **approval for deployment**

---
## **Regression Testing**

Regression Testing is the process of **retesting a software application** after changes (like bug fixes, enhancements, or configuration changes) to ensure that **existing functionality still works correctly**.

In other words:  
**“Did the new change break anything that used to work?”**

### **2. Purpose of Regression Testing**

- Detect unintended side-effects caused by code changes
- Ensure **previously tested features** continue to function as expected
- Maintain **software quality and stability** over time
- Reduce risk during maintenance and updates

### **3. When to Perform Regression Testing**

- After **bug fixes**
- After **new features or enhancements**
- After **performance improvements or refactoring**
- After **changes in environment or configuration**

### **4. Techniques for Regression Testing**

#### **A. Retest All**

- Run **all existing test cases** again
- Ensures maximum coverage
- **Cons:** Time-consuming and expensive

#### **B. Selective Regression**
- Only test **modules affected by recent changes**
- Efficient but relies on accurate impact analysis
#### **C. Prioritized Regression**

- Test cases are **ranked by criticality or usage frequency**
- High-priority functions tested first

#### **D. Automated Regression Testing**

- Use **testing tools** to run regression tests automatically
- Saves time, especially for large projects
- Examples: Selenium, JUnit, TestNG, QTP/UFT

### **5. Key Concepts**

- **Baseline**: Original, stable version of the software
- **Impact Analysis**: Identify which modules/functions may be affected by changes
- **Regression Test Suite**: Collection of test cases designed specifically for regression testing
- **Automation**: Highly recommended for frequent regression tests

### **6. Example Scenario**

Suppose an **online shopping system** adds a new “discount coupon” feature:

- Regression tests check that **login, search, cart, payment, and order confirmation** still work correctly.
- Ensures new feature doesn’t break **existing functionality**.

### **7. Benefits of Regression Testing**

- Maintains **software integrity** after changes
- Detects bugs that may have been **introduced accidentally**
- Supports **frequent releases and agile development**
- Increases **confidence in software stability**
- Reduces **cost of maintenance** in the long run

--- 
# **Alpha and Beta Testing**

Alpha Testing is a type of **acceptance testing performed by internal staff** before releasing software to real users.  
It is usually done in a **controlled environment** to identify bugs, usability issues, and missing requirements.

- Focused on **detecting errors early**
- Simulates real user behavior but within the development organization

### **2. Purpose of Alpha Testing**

- Identify **bugs or defects** before external release
- Evaluate **software usability and functionality**
- Ensure **compliance with requirements**
- Provide a **feedback loop** for developers

### **3. Who Performs Alpha Testing?**

- Done by **internal testers, QA team, or employees** who are **not part of development**
- Sometimes involves select internal users for realistic feedback

### **4. Characteristics of Alpha Testing**

- Conducted **before beta testing**
- Performed in a **controlled environment**
- Helps find **critical issues early**
- Often iterative: developers fix defects, then testers re-evaluate

### **5. What is Beta Testing?**

Beta Testing is the **final testing phase** where the software is released to a **limited external audience** (real users).

- Focused on **real-world usage and feedback**
- Detects issues that may not be apparent in a controlled environment
- Ensures the software works on **different hardware, environments, and usage patterns**

### **6. Purpose of Beta Testing**

- Collect **user feedback** before full-scale release
- Identify **unexpected errors or usability issues** in real scenarios
- Validate that the system meets **user expectations and business requirements**
- Reduce the risk of **post-release failures**

### **7. Who Performs Beta Testing?**

- Performed by **end-users or a selected group of customers**
- Often organized as **open beta** (anyone can participate) or **closed beta** (limited testers)

### **8. Key Differences: Alpha vs Beta Testing**

| Feature      | Alpha Testing                      | Beta Testing                              |
| ------------ | ---------------------------------- | ----------------------------------------- |
| Conducted by | Internal staff / QA team           | Actual users / external audience          |
| Environment  | Controlled                         | Real-world / user environment             |
| Purpose      | Catch bugs before external release | Gather real user feedback & usability     |
| Stage        | Before beta testing                | After alpha testing, before final release |
| Feedback     | Faster, iterative                  | Slower, more real-world insights          |
| Scope        | Limited to internal scenarios      | Broader, includes varied environments     |

### **9. Example Scenario**

For an **e-commerce website**:

- **Alpha Test:** Internal testers check login, search, cart, payment, and reports any bugs.
- **Beta Test:** Selected real customers try placing orders, using different devices and browsers, and provide feedback.

Alpha testing helps **catch critical errors internally**, while beta testing ensures the software is **user-ready** in real-world conditions.

--- 
## **White Box and Black Box Testing**

Software testing techniques are broadly categorized into **White Box Testing** and **Black Box Testing**.  
The main difference is whether the **internal code logic is known or not** to the tester.

- **White Box Testing:** Tester knows the **internal structure and logic**.
- **Black Box Testing:** Tester focuses only on **inputs and outputs**, without knowledge of internal code.

### **2. White Box Testing**

White Box Testing (also called **Glass Box, Open Box, or Structural Testing**) is a method where testers **look inside the code** to design test cases.  
The goal is to ensure **every path, branch, and condition** works as intended.

#### **Purpose**

- Verify internal logic of code
- Test all possible paths and conditions
- Detect hidden errors like **loops, branches, or conditional mistakes**
- Ensure code meets design specifications

#### **Techniques**

- **Statement Coverage:** Every statement is executed at least once
- **Branch Coverage:** Every branch of a decision is tested
- **Path Coverage:** All possible paths through the program are tested
- **Condition Coverage:** All logical conditions are evaluated both true and false

#### **Advantages**

- Finds hidden errors in the code
- Optimizes code quality and structure
- Effective for critical modules

#### **Limitations**

- Requires programming knowledge
- Time-consuming for large applications
- Cannot catch missing functionalities

### **3. Black Box Testing**

Black Box Testing (also called **Behavioral or Functional Testing**) tests software **without knowing internal code**.  
Focuses on **what the software does**, not how it does it.

#### **Purpose**

- Validate software against **requirements**
- Detect incorrect or missing functionality
- Ensure expected outputs for given inputs

#### **Techniques**

- **Equivalence Partitioning:** Group inputs with similar behavior, test one representative from each
- **Boundary Value Analysis:** Test at, above, and below the input boundaries
- **Decision Table Testing:** Tests all combinations of input conditions
- **State Transition Testing:** Tests system behavior for different states

#### **Advantages**

- Easy to design tests without programming knowledge
- Focuses on user requirements
- Detects missing functionalities

#### **Limitations**

- Cannot check internal code logic
- Limited coverage for internal paths
- Difficult to design exhaustive tests for complex systems

### **4. Comparison Table: White Box vs Black Box**

| Feature           | White Box Testing                                 | Black Box Testing                                                                    |
| ----------------- | ------------------------------------------------- | ------------------------------------------------------------------------------------ |
| Knowledge of code | Required                                          | Not required                                                                         |
| Focus             | Internal logic, code structure                    | Functional behavior, requirements                                                    |
| Tester            | Developer / tester with coding knowledge          | Tester / end-user                                                                    |
| Techniques        | Statement, Branch, Path, Condition coverage       | Equivalence partitioning, Boundary value analysis, Decision tables, State transition |
| Purpose           | Verify code correctness                           | Verify software functionality                                                        |
| Advantages        | Finds hidden bugs, optimizes code                 | Validates requirements, detects missing features                                     |
| Limitations       | Cannot find missing functionality, time-consuming | Cannot test internal paths, limited coverage                                         |

### **5. Example Scenario**

For an **online banking system**:

- **White Box Testing:** Check if the transfer function correctly executes all code paths for debit and credit logic.
- **Black Box Testing:** Verify that a user can successfully transfer money using the interface, without looking at the code.

--- 
## **Introduction to Software Maintenance**

Software Maintenance is the process of **modifying a software system after it has been delivered** to correct faults, improve performance, or adapt it to a changed environment.  
It ensures that software continues to **meet user needs and remains reliable** over time.

Basically:  
**“Keep the software alive, updated, and useful after release.”**

### **2. Importance of Software Maintenance**

- **Correct errors** that were missed during testing
- **Adapt software** to new hardware, OS, or business environments
- **Enhance features** based on user feedback
- **Improve performance** or maintain efficiency
- **Extend software life** and reduce total cost

Studies show **maintenance can take 40–70% of total software costs**, making it a critical activity.

### **3. Objectives of Software Maintenance**

- **Corrective Maintenance:** Fix defects or bugs discovered after deployment
- **Adaptive Maintenance:** Modify software to work in a **new or changed environment**
- **Perfective Maintenance:** Improve **performance, maintainability, or user experience**
- **Preventive Maintenance:** Make changes to **prevent future problems** or failures

### **4. Types of Software Maintenance**

#### **A. Corrective Maintenance**

- Fixes errors, faults, or bugs
- Example: Patch to correct a login failure

#### **B. Adaptive Maintenance**

- Updates software to match **new operating systems, platforms, or hardware**
- Example: Upgrading software to run on a new version of Windows

#### **C. Perfective Maintenance**

- Enhances software based on **user requests or feedback**
- Example: Adding a new search filter in an e-commerce app

#### **D. Preventive Maintenance**

- Proactively improves software to **avoid future issues**
- Example: Refactoring code to reduce complexity and improve reliability

### **5. Challenges in Software Maintenance**

- Understanding **legacy code** without original documentation
- Ensuring **changes do not introduce new bugs**
- Managing **complex interdependencies** between modules
- Allocating **resources and time** for ongoing maintenance
- Balancing **enhancements and corrective work**

---

### **6. Best Practices in Software Maintenance**

- Maintain **accurate documentation**
- Follow **coding standards and guidelines**
- Use **version control systems**
- Conduct **regression testing** after changes
- Prioritize changes based on **criticality and impact**
- Ensure **communication between developers and users**

### **7. Example Scenario**

For an **online banking system**:

- **Corrective:** Fix bug in funds transfer
- **Adaptive:** Make software compatible with a new mobile OS
- **Perfective:** Add a feature for transaction categorization
- **Preventive:** Refactor code to improve scalability for future growth

--- 
## **Types of Software Maintenance**

Software Maintenance is divided into **four main types**, based on the purpose of the change. Each type addresses different aspects of keeping software functional, efficient, and relevant.

### **1. Corrective Maintenance**

- **Purpose:** Fix **defects or errors** found after software release.
    
- **Goal:** Ensure the software functions correctly according to its original requirements.
   
- **Examples:**
    
    - Correcting a bug in the login module
    - Fixing calculation errors in a billing system

- **Notes:**
    
    - Usually reactive, performed after a fault is reported
    - Does not enhance functionality or performance

### **2. Adaptive Maintenance**

- **Purpose:** Modify software to work in a **changed environment**.
- **Goal:** Keep the software compatible with new **hardware, operating systems, platforms, or business environments**.
- **Examples:**
    
    - Updating a mobile app for a new version of iOS/Android
    - Making desktop software compatible with a new Windows version

- **Notes:**
    
    - Ensures software remains usable even when external conditions change

### **3. Perfective Maintenance**

- **Purpose:** **Improve performance, usability, or maintainability** based on user feedback or new requirements.
- **Goal:** Enhance the software without changing its core functionality.

- **Examples:**
    
    - Adding a new search filter in an e-commerce website
    - Improving response time of a report generation module

- **Notes:**
    
    - Often driven by customer requests or evolving business needs
    - Focuses on optimization and enhancement

### **4. Preventive Maintenance**

- **Purpose:** **Prevent future problems** by making software more robust and maintainable.

- **Goal:** Reduce the likelihood of errors or failures in the future.

- **Examples:**
    
    - Refactoring code to reduce complexity
    - Updating documentation for better understanding

- **Notes:**
    
    - Proactive maintenance
    - Improves software longevity and maintainability

### **5. Summary Table**

| Type       | Purpose                          | Example                              | Nature                |
| ---------- | -------------------------------- | ------------------------------------ | --------------------- |
| Corrective | Fix defects                      | Bug fix in login                     | Reactive              |
| Adaptive   | Adjust to environment changes    | Update for new OS                    | Reactive / Adaptive   |
| Perfective | Enhance performance or usability | Add new feature, optimize speed      | Proactive / Enhancing |
| Preventive | Prevent future problems          | Refactor code, improve documentation | Proactive             |

--- 
# **Forward and Reverse Engineering**

### **1. Forward Engineering**

- **Definition:** Forward engineering is the **traditional process of developing software** starting from **requirements**, then moving to **design, coding, testing, and deployment**.

- It’s the **normal software development lifecycle** from scratch.

- **Purpose:** Transform user needs and requirements into a working software system.

- **Steps:**
    
    1. Requirement Analysis
    2. System Design
    3. Implementation (Coding)
    4. Testing
    5. Deployment & Maintenance
	
- **Example:** Creating a new banking system based on client specifications.

**Key Points:**

- Goes **from abstract to concrete**
- Produces software **from scratch**
- Emphasizes **planning, design, and structured development**

### **2. Reverse Engineering**

- **Definition:** Reverse engineering is the process of **analyzing an existing software system** to identify its **components, architecture, and design**, often to **recreate documentation or reproduce the system**.
   
- Useful when **documentation is missing or outdated**, or when updating/maintaining legacy systems.

- **Purpose:**
    
    - Understand how software works internally
    - Rebuild documentation
    - Facilitate maintenance, enhancement, or migration

- **Example:** Analyzing an old inventory system to create proper design documents for modernization.

**Key Points:**

- Goes **from concrete (code) to abstract (design)**
- Helps in **software maintenance and reengineering**
- Can be used to **improve or upgrade legacy software**

### **3. Comparison Table: Forward vs Reverse Engineering**

| Feature   | Forward Engineering          | Reverse Engineering                        |
| --------- | ---------------------------- | ------------------------------------------ |
| Direction | Requirements → Design → Code | Code → Design → Documentation              |
| Purpose   | Create new software          | Understand/maintain existing software      |
| Process   | Normal SDLC steps            | Analysis of existing system                |
| Output    | Working software             | Design documentation, system understanding |
| Usage     | New development              | Maintenance, legacy system upgrades        |
| Nature    | Proactive                    | Reactive / Investigative                   |

Forward engineering is **creating new software from scratch**, while reverse engineering is **working backward to understand or improve existing software**.


--- 
# **Software Re-engineering**

### **1. What is Software Re-engineering?**

Software Re-engineering is the process of **analyzing, modifying, and improving an existing software system** to **enhance maintainability, performance, or functionality** without completely rewriting it from scratch.

It often follows **reverse engineering** — first, you understand the system, then you improve it.

### **2. Purpose of Software Re-engineering**

- Improve **software quality and maintainability**
- Reduce **maintenance cost** compared to building a new system
- Update software to **meet current user requirements**
- Make software **compatible with new platforms or technologies**
- Eliminate **redundant, obsolete, or inefficient code**

### **3. Activities in Software Re-engineering**

1. **Reverse Engineering:** Analyze the existing system to understand its structure and design
2. **Code Restructuring:** Improve code readability and maintainability without changing functionality
3. **Data Re-engineering:** Update or migrate databases to modern formats or structures
4. **Design Modification:** Enhance system design for better performance, scalability, or modularity
5. **Testing & Validation:** Ensure that modifications do not break existing functionality

### **4. Types of Re-engineering**

- **Code Re-engineering:** Refactor or rewrite parts of the code for efficiency and maintainability
- **Data Re-engineering:** Transform or migrate data structures, databases, or formats
- **Design Re-engineering:** Redesign system architecture to improve quality and adaptability

### **5. Benefits of Software Re-engineering**

- Reduces **long-term maintenance cost**
- Improves **system performance and reliability**
- Extends **software life** without full redevelopment
- Enables adaptation to **new technologies or environments**
- Helps in **documenting legacy systems**


### **6. Example Scenario**

Suppose a **legacy payroll system** runs on outdated hardware and has no proper documentation:

1. Reverse engineer to **understand existing code and logic**
2. Restructure code for **better readability and maintainability**
3. Upgrade database and interfaces to **modern standards**
4. Test the system thoroughly before deploying the **enhanced version**


Software Re-engineering is essential in modern software practice because it **bridges legacy systems with current technological requirements** efficiently.

--- 
--- 
--- 