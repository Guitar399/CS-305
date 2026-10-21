CS 305: Software Security - Artemis Financial Portfolio

Overview

This repository contains the software security portfolio artifacts for Artemis Financial, completed as part of the CS 305 Software Security course. The project focuses on conducting a comprehensive vulnerability assessment, evaluating third-party dependencies, refactoring legacy Java source code, and applying secure coding practices to harden a RESTful web application.

1. Client Summary & Software Requirements

Artemis Financial is a financial services and consulting firm specializing in wealth management, financial planning, and advisory services. Their software handles sensitive personal and financial data—including savings, investments, and insurance plans—for clients around the world.

The company required an evaluation and modernization of their legacy web application to:

Ensure secure, encrypted communications across international transactions.

Comply with strict data protection and privacy regulations (e.g., GLBA, FINRA, GDPR).

Harden their RESTful API against external threats such as Man-in-the-Middle (MitM) attacks, Cross-Site Scripting (XSS), SQL injection, and unauthorized data access.

2. Vulnerability Assessment & Importance of Secure Coding

Through a combination of manual source code review and static dependency analysis, several critical vulnerabilities were identified:

Transport Layer Flaws: Lack of HTTPS configuration in application.properties, exposing traffic to interception.

Denial of Service (DoS): Unrestricted file upload size limits (215MB threshold).

Injection & XSS Risks: Unsanitized request inputs in GreetingController.java and unconstrained HTTP verb mappings in CRUDController.java.

Encapsulation & Concurrency Issues: Package-private field visibility, lack of negative deposit checks, and non-synchronized state modifications in Customer.java.

Known Dependency Vulnerabilities: Outdated libraries containing critical vulnerabilities such as Spring4Shell (CVE-2022-22965), Ghostcat (CVE-2020-1938), and Bouncy Castle key generator weaknesses (CVE-2018-1000180, CVE-2020-15522).

Why Secure Coding Matters

Coding securely is vital because software errors and unpatched third-party dependencies can lead to catastrophic data breaches, financial loss, and severe regulatory penalties. Implementing security early in the development lifecycle preserves client trust, protects corporate reputation, and safeguards critical financial assets.

3. Challenging and Helpful Aspects of the Assessment

Challenging Aspect: Identifying subtle architectural and configuration issues—such as missing SSL/TLS properties in configuration files and recognizing weak package-private variable visibility in domain models—required detailed, manual code inspection.

Helpful Aspect: Tracing data flows through API controllers bridged theoretical security concepts with practical code analysis, demonstrating how unvalidated parameters directly introduce security risks.

4. Increasing Layers of Security & Future Assessment Tools

To apply defense-in-depth, the following security layers were introduced:

Transport Layer Security: Enforcing HTTPS via PKCS12 keystore configuration on port 8443.

Resource Limits: Constraining multipart file upload limits to 5MB to prevent DoS attacks.

API Hardening: Binding endpoints to explicit HTTP verbs (e.g., @GetMapping) and sanitizing request parameters.

Defensive Programming: Encapsulating domain fields with private access modifiers, adding validation logic, and synchronizing financial transaction methods.

Future Assessment Workflow

In future software tasks, I will utilize automated Static Application Security Testing (SAST) tools, Software Composition Analysis (SCA) via OWASP Dependency-Check, and framework guidelines (such as the OWASP Top 10) to systematically detect and remediate risks.

5. Ensuring Functionality and Security Post-Refactoring

To ensure the application remained fully functional following refactoring:

Logic Verification: Refactored methods—such as the encapsulated and synchronized deposit() method in Customer.java—were tested to ensure accurate accounting logic and proper error handling for invalid inputs.

Regression Testing: Re-running static dependency checks and security code reviews confirmed that code modifications addressed existing vulnerabilities without introducing new security flaws or breaking API endpoints.

6. Resources, Tools, and Secure Coding Practices

OWASP Top 10 & Guidelines: Provided standard vulnerability classifications and remediation strategies.

OWASP Dependency-Check & Maven: Used to identify transitive dependencies and update pom.xml libraries (e.g., updating Spring Boot and Bouncy Castle dependencies).

Secure Design Patterns: Implemented encapsulation, parameter sanitization, parameterized queries, and thread safety (synchronized).

7. Value to Future Employers

This repository demonstrates my practical capability to perform professional vulnerability assessments, analyze source code and build manifests, and execute targeted security remediations. The included Artemis Financial Vulnerability Assessment Report serves as a concrete example of my ability to secure enterprise software applications and write resilient, defensive code.
