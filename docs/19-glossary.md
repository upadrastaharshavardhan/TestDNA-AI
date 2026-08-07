# 📚 TestDNA-AI Glossary

> **The Common Language of AI-Powered Quality Engineering**

**Version:** 1.0.0  
**Status:** Reference Documentation

---

# Introduction

This glossary defines the terminology used throughout the TestDNA-AI platform.

As the platform introduces new concepts such as **DNA Profiles**, **Engineering Memory**, **Repository Intelligence**, and **AI Agents**, a shared vocabulary helps contributors, architects, QA engineers, developers, and enterprise teams understand the system consistently.

---

# A

## Agent

A specialized AI component responsible for a single engineering capability.

Examples:

- Memory Agent
- Requirement Agent
- Failure Intelligence Agent
- Coverage Agent

Unlike a traditional chatbot, an Agent has a clearly defined responsibility, limited permissions, and dedicated reasoning capabilities.

---

## Agent Orchestrator

The central coordinator responsible for selecting, sequencing, and combining multiple AI agents to solve complex engineering tasks.

It does not perform domain reasoning itself but delegates work to specialized agents.

---

## AI Copilot

The conversational interface of TestDNA-AI.

The Copilot answers engineering questions using organizational knowledge, semantic search, the knowledge graph, and AI agents.

---

## API Intelligence

The capability of understanding API definitions, endpoints, request/response structures, dependencies, and how automation interacts with backend services.

---

## Architecture Review

An automated analysis of test automation projects to evaluate structure, maintainability, naming conventions, and adherence to engineering standards.

---

# B

## Business Capability

A functional area of the application that provides business value.

Examples:

- Login
- Checkout
- Customer Registration
- Payments
- Order Tracking

DNA Profiles map automation assets to business capabilities.

---

## BM25

A keyword-based search ranking algorithm commonly combined with vector search to create Hybrid Search.

---

# C

## Confidence Score

A numerical indication of how reliable an AI recommendation is.

Confidence is influenced by:

- Retrieved evidence
- Repository coverage
- DNA similarity
- Historical executions
- Knowledge Graph connectivity

Higher confidence indicates stronger supporting evidence.

---

## Context

The collection of information available during AI reasoning.

Context may include:

- Repository
- Requirement
- User
- Branch
- Pull Request
- Historical executions
- DNA Profiles
- Related assets

---

## Coverage

The degree to which requirements, business capabilities, APIs, or application functionality are validated by automation.

---

## Coverage Gap

A requirement or feature that lacks sufficient automated validation.

---

# D

## DNA Engine

The core intelligence component that analyzes automation assets and extracts structured metadata.

It transforms tests into reusable knowledge.

---

## DNA Profile

A structured representation of an automation asset.

A DNA Profile captures:

- Business capability
- Framework
- Programming language
- APIs
- Page Objects
- Assertions
- Dependencies
- Reuse score
- Stability metrics

DNA Profiles allow TestDNA-AI to compare automation semantically instead of treating it as plain text.

---

## Duplicate Automation

Automation that validates functionality already covered by existing tests.

One of the platform's primary goals is to prevent unnecessary duplication.

---

# E

## Embedding

A numerical vector representation of text or code used for semantic similarity.

Embeddings power semantic search and AI retrieval.

---

## Engineering Memory

The persistent organizational knowledge accumulated from:

- Requirements
- Test cases
- Automation
- Executions
- Failures
- Reviews
- Releases

Engineering Memory is one of the foundational concepts of TestDNA-AI.

---

## Explainable AI

AI recommendations that include:

- Supporting evidence
- Confidence score
- Reasoning summary
- Source references

The platform avoids opaque recommendations whenever possible.

---

# F

## Failure Intelligence

The capability to classify, explain, and recommend actions for automation failures using historical data and execution evidence.

---

## Framework Intelligence

The platform's understanding of different automation frameworks, including their structure, conventions, and reusable patterns.

---

# G

## Graph Traversal

The process of navigating relationships within the Knowledge Graph to discover connected engineering assets.

---

# H

## Hybrid Search

A search strategy that combines:

- Keyword search (BM25)
- Semantic vector search
- Metadata filtering

Hybrid Search improves precision and recall.

---

# I

## Impact Analysis

The process of identifying which tests, APIs, pages, or business capabilities are affected by a proposed change.

---

## Indexing

The process of scanning repositories and creating searchable representations of engineering assets.

---

# K

## Knowledge Graph

A graph database containing relationships between engineering artifacts.

Examples:

Requirement → Test → API → Execution → Failure

The Knowledge Graph enables dependency analysis and explainable AI.

---

# L

## LLM (Large Language Model)

A machine learning model capable of understanding and generating natural language.

TestDNA-AI is model-agnostic and can integrate with multiple LLM providers.

---

# M

## Memory Agent

An AI agent responsible for discovering reusable automation and preserving organizational engineering knowledge.

---

## Metadata

Structured information describing an engineering artifact.

Examples:

- Author
- Framework
- Tags
- Repository
- Business capability
- Execution history

---

# O

## Organizational Intelligence

The collective engineering knowledge accumulated across repositories, teams, and projects.

Unlike individual expertise, Organizational Intelligence remains available even when teams change.

---

# P

## Plugin

An extension that adds new capabilities to TestDNA-AI without modifying the core platform.

Examples:

- Repository connectors
- AI integrations
- Reporting modules
- Framework support

---

## Pull Request Intelligence

Analysis of pull requests to identify impacted automation, potential risks, and recommended regression suites.

---

# Q

## Quality Engineering

A holistic approach to software quality that combines testing, automation, risk analysis, observability, and continuous improvement.

TestDNA-AI is designed to support the entire Quality Engineering lifecycle.

---

## Query Understanding

The ability of the AI Copilot to interpret user intent rather than relying solely on keyword matching.

---

# R

## RAG (Retrieval-Augmented Generation)

An AI technique that combines retrieval of relevant organizational knowledge with language model generation.

RAG helps produce grounded, evidence-backed responses.

---

## Regression Optimization

The process of selecting the most relevant subset of automated tests based on code changes, dependencies, and historical execution data.

---

## Repository Intelligence

The capability to understand the structure, contents, technologies, and relationships within software repositories.

Repository Intelligence serves as the foundation for many TestDNA-AI features.

---

## Reuse Score

A metric estimating how suitable an existing automation asset is for reuse in a new context.

---

# S

## Semantic Search

A search capability that understands intent and meaning rather than exact keywords.

It enables engineers to discover relevant assets even when different terminology is used.

---

## Similarity Score

A measure of how closely two automation assets resemble one another based on their DNA Profiles and semantic characteristics.

---

# T

## TestDNA

The unique structural and semantic fingerprint of an automation asset.

It represents what the automation does rather than how it is written.

---

## Traceability

The ability to connect requirements, automation, executions, failures, pull requests, and releases through explicit relationships.

---

# V

## Vector Database

A specialized database that stores embeddings and enables efficient semantic similarity searches.

Examples include Qdrant, Milvus, Pinecone, and Weaviate.

---

# W

## Workflow

A sequence of activities performed by the platform to achieve a specific outcome.

Examples:

- Repository indexing
- DNA extraction
- Semantic search
- AI recommendation generation
- Failure investigation

---

# Z

## Zero Trust

A security principle in which no user, service, or component is automatically trusted.

Every request must be authenticated, authorized, and validated.

---

# Acronyms

| Acronym | Meaning |
|----------|---------|
| AI | Artificial Intelligence |
| API | Application Programming Interface |
| BM25 | Best Matching 25 Ranking Algorithm |
| CI | Continuous Integration |
| CD | Continuous Delivery |
| DNA | Digital Knowledge Fingerprint of Automation Assets |
| IDE | Integrated Development Environment |
| LLM | Large Language Model |
| MCP | Model Context Protocol |
| POM | Page Object Model |
| QA | Quality Assurance |
| QE | Quality Engineering |
| RAG | Retrieval-Augmented Generation |
| RBAC | Role-Based Access Control |
| REST | Representational State Transfer |
| SDK | Software Development Kit |
| SSO | Single Sign-On |
| UI | User Interface |
| UX | User Experience |

---

# Guiding Philosophy

Many of the terms in this glossary describe concepts that extend beyond traditional test automation.

TestDNA-AI is founded on the belief that software quality improves when engineering knowledge is preserved, connected, searchable, and continuously enhanced through explainable AI.

This glossary will evolve alongside the platform, providing a shared vocabulary for contributors, users, and organizations adopting TestDNA-AI.
