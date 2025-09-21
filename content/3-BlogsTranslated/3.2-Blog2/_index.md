---
title: "Blog 2"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---

# Enabling customers to deliver production-ready AI agents at scale

AI agents are ushering in a major technological revolution, similar to the birth of the Internet. AWS is committed to building the best platform for developing and deploying secure, reliable, and scalable AI agents. Real-world applications have demonstrated great potential in healthcare (AstraZeneca), finance (Yahoo Finance), and agriculture (Syngenta). To expand on this success, AWS is focused on providing tools and platforms that make it easy for organizations to move AI agents from prototype to production, with a focus on security, reliability, and adaptability over time.

---

## Guiding Principles for Agentic AI

AWS structures its approach around **four core principles**:

1. **Embrace Agility**  
   Build systems that are flexible, modular, and able to evolve as models, capabilities, and requirements change. :contentReference[oaicite:3]{index=3}

2. **Evolve Fundamentals**  
   Tailor core infrastructure elements for the agentic era, including:  
   - Security & Trust (session isolation, memory isolation) :contentReference[oaicite:4]{index=4}  
   - Reliability & Scalability (checkpointing, recovery, scaling to many concurrent sessions) :contentReference[oaicite:5]{index=5}  
   - Identity (fine-grained permissions, integrating with identity providers) :contentReference[oaicite:6]{index=6}  
   - Observability (real-time monitoring, telemetry) :contentReference[oaicite:7]{index=7}  
   - Data access & use, including integrating proprietary data securely :contentReference[oaicite:8]{index=8}  
   - Seamless Integration with existing tools, clouds, agents, APIs etc. :contentReference[oaicite:9]{index=9}  

3. **Deliver Superior Outcomes with Model Choice & Data**  
   - Allow customers to choose what model(s) fit their needs (reasoning, speed, cost, etc.). :contentReference[oaicite:10]{index=10}  
   - Provide tools for model customization: fine-tuning, alignment, pre/post training, etc. :contentReference[oaicite:11]{index=11}  
   - Introduce solutions like Amazon Nova customization (including PEFT, full fine-tuning, etc.) and Nova Act for browser-based agents. :contentReference[oaicite:12]{index=12}  
   - Introduce **Amazon S3 Vectors** for storing vector embeddings more cheaply while maintaining performance, enabling richer context and memory for agents. :contentReference[oaicite:13]{index=13}

4. **Deploy Solutions that Transform Experiences**  
   - Provide pre-built agentic solutions and tools, so organizations don’t need to build everything from scratch. :contentReference[oaicite:14]{index=14}  
   - Use AWS Marketplace to access curated agents/tools. :contentReference[oaicite:15]{index=15}  
   - Examples: Kiro (IDE for spec-driven development), AWS Transform (agents for code analysis, modernization tasks), Amazon Connect with AI for customer interactions. :contentReference[oaicite:16]{index=16}

---

## New Capabilities & Announcements

- **AgentCore**: a set of services for deploying and operating agents at enterprise scale — with runtime, identity, observability, memory, browser, code interpreter tools, etc. :contentReference[oaicite:17]{index=17}  
- **Nova Customization in SageMaker AI**: expanded capabilities for pre-training, fine-tuning, alignment using various techniques to customize models. :contentReference[oaicite:18]{index=18}  
- **Nova Act SDK**: browser-automation-focused agents, currently in preview. :contentReference[oaicite:19]{index=19}  
- **S3 Vectors**: native vector support in S3, reducing vector storage cost by ~90% while keeping low latency query. :contentReference[oaicite:20]{index=20}  
- **Marketplace Agents & Tools**: curated catalog of agents & tools from AWS Partners, simpler procurement and deployment. :contentReference[oaicite:21]{index=21}  
- **Pre-built Solutions**: tools like Kiro and AWS Transform to accelerate moving from concept to production. :contentReference[oaicite:22]{index=22}

---

## Recommendations & Path Forward

- Start now: pick a specific business problem to prototype. Don’t wait for perfect conditions. :contentReference[oaicite:23]{index=23}  
- Collect real-world feedback and iterate quickly. :contentReference[oaicite:24]{index=24}  
- AWS is investing heavily (e.g. Generative AI Innovation Center) to support customers. :contentReference[oaicite:25]{index=25}

---

## Conclusion

AWS is laying down a comprehensive foundation to enable organizations to build, customize, secure, and scale AI agents. With new tools and services (AgentCore, Nova, S3 Vectors, etc.), the focus is on moving beyond experiments into production systems, ensuring trustworthiness, adaptability, and business value.


