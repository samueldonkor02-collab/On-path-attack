Path Attacks Lab: A Comprehensive Security Assessment

Executive Summary

Over the past weeks, I've been working through a hands-on cybersecurity lab focused on path traversal vulnerabilities and directory enumeration attacks. This project demonstrates my foundational understanding of web application security testing, my ability to use industry-standard penetration testing tools, and my commitment to building a career in cybersecurity—all while maintaining honest awareness of where I am in my learning journey.

Project Overview

The Challenge

I conducted a security assessment of the OWASP Juice Shop, a deliberately vulnerable web application designed for security training. My objective was to identify and document path-based vulnerabilities that could allow unauthorized access to restricted files and directories.

The Approach

I configured and utilized Burp Suite Community Edition (v2022.12.5), the industry-standard web application security testing platform, to:

Intercept and analyze HTTP/HTTPS traffic
Identify potential path traversal vectors
Test for improper input validation on file paths and directory navigation
Document findings and vulnerability chains
Technical Implementation

1. Environment Setup

Target Application: OWASP Juice Shop (intentionally vulnerable e-commerce platform)
Testing Platform: Burp Suite Community Edition v2022.12.5
Proxy Configuration: Configured proxy listener on 127.0.0.1:8080 with loopback-only binding for secure, isolated testing
Operating System: Kali Linux (penetration testing distribution)
2. Proxy Configuration & Traffic Interception

I configured Burp Suite's proxy listener with the following specifications:

Binding: Port 8080, restricted to localhost (127.0.0.1)
Request Handling: Enabled interception of client requests based on specific rules
TLS/SSL Configuration: Implemented certificate handling for HTTPS traffic analysis
Intercept Rules: Configured selective interception based on:
File extensions
HTTP methods (GET, POST, etc.)
URL patterns
Request parameters
This setup allows me to capture, analyze, and modify requests in real-time—critical for identifying how the application handles user input in file paths and directory references.

3. Vulnerability Assessment

From my initial scans (visible in the scan results), I identified multiple endpoints and analyzed them for:

Directory Traversal: Testing for ../ sequences that might escape intended directories
Path Normalization Issues: Checking how the application processes encoded paths
Access Control Bypass: Attempting to reach resources outside the intended scope
File Enumeration: Identifying which files and directories are accessible through path manipulation
What I've Learned (Honestly)

Strengths & Progress

✅ Technical Competencies Developed:

Hands-on experience with Burp Suite (the gold standard in penetration testing)
Understanding of HTTP request/response cycles and how web applications handle file paths
Ability to configure security testing infrastructure properly
Familiarity with common vulnerability patterns (OWASP Top 10 - A01:2021 Broken Access Control)
Working knowledge of proxy-based traffic interception and analysis
✅ Professional Skills:

Learning to document security findings clearly
Understanding the importance of controlled testing environments
Building habits around careful, methodical security analysis
Recognizing the ethical responsibility of security testing
Where I'm Still Growing

🟡 Areas of Continued Development:

Exploitation Depth: While I understand path traversal concepts, I'm still developing expertise in chaining multiple vulnerabilities together
Advanced Burp Suite Features: I'm comfortable with core proxy functionality but still learning the Scanner, Intruder, and Repeater tools for more sophisticated testing
Vulnerability Remediation: Understanding how to fix these vulnerabilities is something I'm actively studying alongside learning to find them
Real-World Application Context: Most of my experience is in controlled lab environments; understanding vulnerabilities in complex production systems requires continued growth
Why This Background Matters

Coming from a healthcare background, I bring valuable perspectives to cybersecurity:

Understanding Compliance & Risk: Healthcare shaped my mindset around data protection, regulatory requirements (HIPAA), and the real consequences of security failures
Attention to Detail: Medical precision translates directly to security work—one missed vulnerability can have serious consequences
Responsibility Mindset: In healthcare, errors cost lives. In security, errors cost companies and users. I approach both with appropriate gravity
This career transition isn't a pivot away from my values—it's applying them to a field where they're equally critical.

What This Project Demonstrates

For Employers, This Shows I Can:

✅ Learn and use complex security tools independently
✅ Set up secure testing environments correctly
✅ Think like an attacker (essential for defensive security)
✅ Document work in a professional manner
✅ Understand web application security fundamentals
✅ Commit to continuous learning in a rapidly evolving field
What I'm NOT Claiming:

❌ I'm not an expert penetration tester (I'm 2-3 months in)
❌ I haven't worked on production systems yet
❌ I don't have years of hands-on experience
❌ I'm not ready to lead security initiatives alone
What I AM:

✅ A dedicated learner with real hands-on experience
✅ Someone who understands the fundamentals correctly
✅ Committed to ethical security practices
✅ Ready to grow into a junior security role or apprenticeship
✅ Someone who's honest about where I am in my journey
Next Steps in My Learning

I'm actively working on:

Completing the OWASP Top 10 vulnerabilities through practical lab work
Pursuing industry certifications (CompTIA Security+, CEH foundations)
Building a portfolio of documented labs and write-ups
Contributing to open-source security projects to gain real-world experience
Engaging with the security community through forums, CTF (Capture The Flag) competitions, and local meetups
Closing Statement

This project represents my honest starting point in cybersecurity. I'm not claiming mastery—I'm demonstrating:

Technical competence in using professional tools
Conceptual understanding of common vulnerabilities
Professional discipline in documentation and approach
Genuine commitment to the field, despite being early in my career journey
I'm looking for opportunities where I can continue this learning curve in a professional environment—whether that's a junior security analyst role, a security apprenticeship, or a position supporting a larger security team. I bring the work ethic, attention to detail, and ethical foundation; I'm ready to build the specialized experience.

If you'd like to discuss this project, my approach to learning, or how my healthcare background brings unique perspective to security, I'd welcome the conversation.
