# API Security Fundamentals

## Futher Reading

- [OWASP API Security Project](https://owasp.org/www-project-api-security/)
- [Open Web Application Security Project](https://owasp.org/www-project-top-ten/)
- [API Sec University](https://www.apisecuniversity.com/)
- [API Security Fundamentals Course](https://youtu.be/o6d6BjX-Iys)

## Table of Contents

- [API Security Fundamentals](#api-security-fundamentals)
  - [Futher Reading](#futher-reading)
  - [Table of Contents](#table-of-contents)
  - [API The 3 Pillars of API Security](#api-the-3-pillars-of-api-security)
    - [Governance](#governance)
      - [API Awareness](#api-awareness)
        - [Known your APIs and data](#known-your-apis-and-data)
        - [Know your risks](#know-your-risks)
      - [API Policies \& Processes](#api-policies--processes)
        - [Documentation: OpenAPI Specification (AKA Swagger)](#documentation-openapi-specification-aka-swagger)
        - [Design Guides: Promote Governance, Consistency](#design-guides-promote-governance-consistency)
          - [Example Design Guidelines](#example-design-guidelines)
    - [Testing](#testing)
      - [Testing API Security](#testing-api-security)
      - [Testing Data Security](#testing-data-security)
      - [Business Logic](#business-logic)
    - [Monitoring](#monitoring)
      - [Monitoring Approaches](#monitoring-approaches)
      - [API Discovery](#api-discovery)
      - [Limitations of Monitoring](#limitations-of-monitoring)
      - [Application Security Technology Landscape](#application-security-technology-landscape)
        - [AppSec by System Layers](#appsec-by-system-layers)
      - [Application Security Development Process](#application-security-development-process)
    - [Best Practices](#best-practices)
      - [Do and Do Not](#do-and-do-not)
  - [2023 OWASP API Top 10 Security Risks](#2023-owasp-api-top-10-security-risks)
    - [Broken Object Level Authorization (BOLA)](#broken-object-level-authorization-bola)
    - [Broken Authentication](#broken-authentication)
    - [Broken Object Property Level Authorization](#broken-object-property-level-authorization)
    - [Unrestricted Resource Consumption](#unrestricted-resource-consumption)
    - [Broken Function Level Authorization](#broken-function-level-authorization)
    - [Server-Side Resource Forgery](#server-side-resource-forgery)
    - [Security Misconfiguration](#security-misconfiguration)
    - [Lack of Protection from Automated Threats](#lack-of-protection-from-automated-threats)
    - [Improper Inventory Management](#improper-inventory-management)
    - [Unsafe Consumption of APIs](#unsafe-consumption-of-apis)

---

## API The 3 Pillars of API Security

### Governance

_Developing Secure APIs_
The benefits of API governance are:

- Consistency
- Setting expectations
- Establishing standard processes
- Enforcing security

#### API Awareness

##### Known your APIs and data

- Get a full inventory of your APIs
  - define the purpose, and its owner, and write documentation
- Standardize and enforce the API deployment process
  - The existence of "shadow/rogue" APIs is a sign of weak governance
  - APIs must only deployed in approved ways, with proper validation
  - Enforce governance at the API Gateway and API Marketplace level
- Mandate API documentation
  - Make sure APIs are consistent and reusable
  - Define documentation requirements
- Create API development standards
  - Style guides, authentication requirements, API versioning, Personally Identifiable Information (PII) tracking

##### Know your risks

1. **Identify**: APIs, business flows, data, access paths
2. **Assess**: vulnerabilities, logic flaws, access control, 3rd party risk
3. **Probability**: examine the likelihood of an attack
4. **Impact**: understand the damage, loss, and consequences of an attack
5. **Mitigation**: develop a plan to address the risk

#### API Policies & Processes

- Engineering process
- API Documentation
- Design guides

##### Documentation: OpenAPI Specification (AKA Swagger)

- Not optional
- Industry standard for REST APIs
- Machine-readable (YAML, JSON)
- Aids development and 3rd party integration
- Aids in security testing
- Manually or auto-generated
- Control what is public vs. private
- Retire old documentation — this is a huge threat vector
- Define the API capability (contract)
  - Title, description, version
  - Base-URL
  - Endpoints, paths
  - Requests, response payloads
  - Authentication requirements
  - Parameters, data types
  - Methods

##### Design Guides: Promote Governance, Consistency

- **Authentication**:
  - type (basic, token, certificate)
  - how to implement
- **Authorization**:
  - who has access to what
  - where are policies enforced
  - consider types of authorization (RBAC, ACL, token-scope, etc)
- **Naming Conventions**:
  - URIs as _nouns_
  - Methods as _verbs_
  - pluralization
  - hierarchy
  - case
  - language
  - no jargon/abbreviations
- **Error Codes**:
  - status codes
  - reference ID
  - human-readable messages
- **Versioning**:
  - when to increment/when not
  - types of versions (V1, V1.5, V2)
- **Units, Formats, Standards**:
  - date/time formats
  - timezones

###### Example Design Guidelines

- [Google Cloud API Design Guide](https://cloud.google.com/apis/design)
- [GitLab API Style Guide](https://docs.gitlab.com/ee/development/api_styleguide.html)

---

### Testing

Ensuring APIs are Free of Flaws

#### Testing API Security

- Unsecured endpoints
- Authentication exploits
- Enumeration
- App DOS, rate limiting
- Missing TLS, SSL issues
- Injection, fuzzing
- Fuzzing, input validation
- Server-side request forgery
- Server properties

#### Testing Data Security

- Access control
- Excessive data exposure
- Sensitive data exposure
- Personal, health, bank data must abide to regulatory compliance and data laws
- File, directory exposure
- Encryption at REST
- Data exfiltration

#### Business Logic

- Cross-account access
- API function abuse
- Role-based access control
- Pen-testing

### Monitoring

Detecting Threats in Production

1. Runtime Protection
   - Policy enforcement
   - Authentication
   - Traffic filtering
2. Threat Detection
   - Fraudulent traffic
   - Distributed attacks
   - Incident response
3. Control Validation
   - Verify API controls
   - Uncover anomalies

#### Monitoring Approaches

1. Proactive: Blocking
   - API Gateway
   - Web App Firewall
2. Reactive: Alerting
   - Logging
   - Security Information and Event Management (SIEM)
   - Runtime API Threat Management

#### API Discovery

- Monitoring can aid API inventory efforts
  - Identify API endpoints in use
  - Discover undocumented/unknown APIs
- Comprehensive discovery requires more sources:
  - API Gateway, Web Application Firewall
  - Code repository
  - Application testing, crawling
- Reliance on traffic based-discovery misses:
  - Internal API traffic not seen by the traffic analysis tool
  - Pre-production APIs
  - Unexercised endpoints

#### Limitations of Monitoring

- Difficult to get full visibility
  - Requires sensors on every network segment
- High false positives on threat detection
  - Live traffic contains limited context
  - Difficult to identify data access violations
  - API monitoring tools are typically used only in alert (not blocking)
- SaaS-based monitoring requires sharing traffic with 3rd parties
  - Privacy concerns
  - Bandwidth requirements
- Traffic-blocking solutions can add latency to API requests

#### Application Security Technology Landscape

##### AppSec by System Layers

- Network
  - Firewall
  - Network Access Control (NAC)
  - Threat Protection
  - Deception
- Endpoint
  - Environmental Data Retrieval (EDR)
  - Anti Malware/Virus
  - Vulnerability Management
- Application
  - Static/Dynamic Application Security Testing (SAST / DAST)
  - Software Composition Analysis (SCA)
  - Container Security
  - Web Application Firewall (WAF)
  - API Security
- Data
  - Encryption
  - Data Loss Prevention (DLP)
  - Access Control
- Web/Messaging
  - Email Gateway
  - Web Gateway
- Identity
  - Authentication
  - Product Information Management (PIM)
  - Identity Governance
- Detection
  - Security Information and Event Management (SIEM)
  - Security Orchestration, Automation and Response (SOAR)
  - Incident Response
- Cloud
  - Cloud Access Security Broker (CASB)
  - Infrastructure Security

#### Application Security Development Process

1. Develop
   - **Static Code Analysis:**
   - Code weaknesses
   - Injection flaws
   - Weak authentication
   - Configuration issues
   - Software Composition Analysis:
   - 3rd party vulnerabilities
   - Licensing issues
   - Outdated components
2. Deploy
   - **API Security Testing:**
   - OWASP testing
   - Business logic
   - Authentication testing
   - Authorization testing
   - Attack simulation
     `↑↑↑ Pre-Production ↑↑↑`
     `↓↓↓ Production ↓↓↓`
3. Operate
   - API Gateway:
   - Authentication
   - Authorization (limited)
   - Rate limiting
   - Traffic filtering
   - Logging
   - API Threat Management:
   - Attack detection
   - API discovery
   - Anomaly detection
   - Traffic blocking

**Recommendations:**

- Shift Left: find issues as early in the process as possible
- Test security controls in production
- Automate as much as possible

### Best Practices

1. Enforce API governance and establish central API control
   - Gateway, marketplace platform
   - No API goes live without passing gates (docs, testing, security)
2. Create a comprehensive testing program
   - Test every endpoint across all OWASP attack types and more
   - Evaluate every data object, user type, and function for logic flaws
   - Leverage automation for comprehensive test coverage
3. Implement automated, continuous testing
   - Although APIs rarely change, code & infrastructure does
   - Every release needs functional and security testing
   - Integrate testing into the CI/CD pipeline
4. Develop API security metrics and assess progress
   - Total APIs managed: new, existing, and retired
   - Vulnerabilities: identified, outstanding, and fixed

#### Do and Do Not

- DO validate all inputs (not just the users' inputs)
- DO keep all sensitive stuff out of the code
- DO use Gateways to control access and traffic
- DO require API documentation
- DO expect users/hijackers to find and use undocumented endpoints
- DO continuously test — simulate attacks, test configs, fuzzing, injections, auth, ...
- Do NOT trust anything (inputs/networks)
- Do NOT confuse obfuscation with security
- Do NOT hardcode keys/tokens — keep all sensitive stuff out of the code
- Do NOT reveal useful info in error messages
- Do NOT have hidden/unadvertised features
- Do NOT filter data in the UI — control is at the application/API level
- Do NOT confuse authentication with authorization

## 2023 OWASP API Top 10 Security Risks

### Broken Object Level Authorization (BOLA)

**Description:**

- Involves manipulating IDs to impersonate other users and access data.

**Risk Exposure:**

- Leads to data loss, disclosure, and manipulation.

**Examples:**

- The attacker authenticates as User A and then retrieves data on User B.

**Prevention:**

- Define data access policies and implement associated controls.
- Enforce data access controls at the application logic layer.
- Implement automated testing to find BOLA flaws.

### Broken Authentication

**Description:**

- Weak or poor authentication creates vulnerability when the API is missing security controls or has poorly implemented authentication controls.

**Risk Exposure:**

- Attackers gain control of users' accounts.
- Data theft and unauthorized transactions

**Examples:**

- Weak password requirements
- Credential stuffing: brute force ID/PW
- No CAPTCHA, rate limiting, or lockout controls
- Auth info in URLs (token, passwords)
- Changing passwords w/o verification
- Not validating token expiration, signature, and permissions
- Insecure password storage

**Prevention:**

- Define authentication policies and standards; follow best practices.
- Implement continuous testing.

### Broken Object Property Level Authorization

**Description:**

- Exploiting endpoints by reading and/or modifying the values of objects.
- Mass assignment: the ability to update object elements.
- Excessive data exposure: revealing unnecessary sensitive data.

**Risk Exposure:**

- Reveals protected user data.

**Examples:**

- User is able to set "account-type=premium"
- User search endpoint returns excessive, unnecessary details (name, email address, ID, ...)

**Prevention:**

- Ensure users can only access legitimate, permitted fields.
- Return only the minimum amount of data required for the use case.

### Unrestricted Resource Consumption

**Description:**

- Inadequate traffic control can allow:

1. Mass data retrieval
2. Risk of operation interruption

**Risk Exposure:**

- Denial of service attacks
- Data harvesting

**Examples:**

- Missing/inadequate rate controls
- Execution timeouts
- Max allocation memory
- Max number of files, upload size
- Excessive operations in a single request
- Excessive records returned in a single request

**Prevention:**

- Implement strong traffic controls
- Test effectiveness of traffic controls with stress testing

### Broken Function Level Authorization

**Description:**

- Abuse of API functionality to improperly modify (create, update, delete) objects.
- Often involves replacing passive methods (GET) with active ones (PUT, DELETE)

**Risk Exposure:**

- May be used to escalate privileges.
- Can be exploited to modify account details.

**Examples:**

- Replacing GET with PUT
- Modifying parameters like "role=admin"
- Deleting an invoice
- Setting account balance to = $0

**Prevention:**

- Identify functions that expose high sensitivity capability and develop controls to limit access.
- Implement continuous release testing to ensure proper behavior.

### Server-Side Resource Forgery

**Description:**

- Exploiting URL inputs to make a request to a malicious, 3rd party server.

**Risk Exposure:**

- SSRF creates a channel for malicious requests, data access, or other fraudulent activity.
- Potential for data leaks.

**Examples:**

- The user submits from an un-permitted URL: `localhost://api/user-data`

**Prevention:**

- Validate and sanitize ALL user-supplied information, including URL parameters.
- Validate third-party URL requests made by the API on behalf of the user.
- Ensure communication is only permitted with trusted resources.
- Test API URL effectiveness.

### Security Misconfiguration

**Description:**

- Broad category to encompass a lack of hardening to unnecessary services.
- Use of bots to scan, detect, and exploit misconfigurations.

**Risk Exposure:**

- Misconfigurations can expose sensitive user data.
- Potential for full server compromise.

**Examples:**

- Lack of security hardening
- Improperly configured permissions
- Missing security patches
- Unnecessary features enabled
- Missing TLS
- CORS policy missing/improperly set

**Prevention:**

- Implement hardening procedures.
- Routinely review configurations.
- Implement automated, continuous security testing.

### Lack of Protection from Automated Threats

**Description:**

- Abuse of legitimate business workflow through excessive, automated use.
- Rate limited, captchas are not always effective against fraudulent traffic.
- Rapid IP rotation makes detection difficult.

**Risk Exposure:**

- Loss of critical business activity.

**Examples:**

- Mass, automated ticket purchasing
- High-volume referral bonuses

**Prevention:**

- Identity critical business workflows.
- Implement fraudulent traffic detection and control.
- Setup and automate testing of control mechanisms.

### Improper Inventory Management

**Description:**

- Unauthorized API access via old, unused API versions, or through trusted 3rd parties.

**Risk Exposure:**

- Data/account theft via unretired APIs.
- Exposure of sensitive data via improperly secured 3rd party APIs.

**Examples:**

- Leaving old versions of APIs exposed without proper deprecation procedures
- Unpatched endpoints
- Endpoints with weaker security
- Outdated documentation
- Unnecessarily exposed endpoints
- API access via 3rd party

**Prevention:**

- Deploy/manage all APIs in Gateway.
- Define rules for versioning and retirement.
- Periodically audit 3rd party access.

### Unsafe Consumption of APIs

**Description:**

- Exposures can occur via the use of 3rd party APIs, which are generally trusted. However, 3rd parties can be exploited, which can be used to attack APIs that rely on them.

**Risk Exposure:**

- Data theft, breach, account takeover

**Examples:**

- The Attacker inserts malicious address data into the validation site used by the Client. The Client then fails to validate data and gets exploited.
- The Attacker compromises 3rd party API causing it to respond with a redirect to a malicious site. If the Client blindly follows redirects without validation, then they risk data exposure to untrusted 3rd parties.

**Prevention:**

- Validate data returned by 3rd party APIs.
- Evaluate security controls of 3rd party API.
- Encrypt all API communication.
- Maintain an approved list of known locations where integrated APIs may be redirected.
