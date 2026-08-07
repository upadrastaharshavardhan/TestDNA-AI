# 🌐 API Design Specification

> **Enterprise API Platform for TestDNA-AI**

**Version:** 1.0.0  
**Status:** Architecture Specification  
**Protocol:** REST + WebSocket + Webhooks + MCP (Future)

---

# Overview

The TestDNA-AI API Platform exposes every capability of the system through secure, versioned, and composable APIs.

The API is designed for:

- Web Portal
- VS Code Extension
- CLI
- AI Copilot
- CI/CD Integration
- Enterprise Systems
- Third-party Integrations
- Future AI Agents

Every feature available in the UI is also available through APIs.

The platform follows an **API-First** architecture.

---

# API Design Principles

## API First

Every new feature begins with an API contract before UI implementation.

---

## Resource Oriented

Resources include:

```
Repositories
DNA Profiles
Tests
Requirements
Knowledge Graph
Search
Recommendations
Failures
Executions
Projects
Users
```

---

## Versioned

```
/api/v1/

Future

/api/v2/
```

Versioning ensures backward compatibility.

---

## Stateless

Every request contains all required context.

---

## Secure by Default

Every endpoint requires authentication and authorization.

---

# Base URL

```
https://api.testdna.ai/api/v1
```

---

# Authentication

Supports:

- OAuth2
- JWT
- Microsoft Entra ID
- GitHub OAuth
- Azure DevOps OAuth
- API Keys (Service Accounts)

Example:

```
Authorization: Bearer <JWT_TOKEN>
```

---

# Standard Response

```json
{
  "success": true,
  "data": {},
  "metadata": {
    "requestId": "REQ-48291",
    "processingTime": "142ms"
  }
}
```

---

# Error Response

```json
{
  "success": false,
  "error": {
    "code": "DNA_NOT_FOUND",
    "message": "DNA profile not found",
    "requestId": "REQ-21981"
  }
}
```

---

# API Categories

```
Repositories

Projects

DNA Engine

Knowledge Graph

Semantic Search

AI Copilot

Requirements

Executions

Failures

Analytics

Administration

Webhooks
```

---

# Repository APIs

## Register Repository

```
POST /repositories
```

```json
{
  "name": "edge-ui",
  "provider": "github",
  "url": "https://github.com/company/edge-ui"
}
```

Response

```json
{
  "repositoryId":"REP-1001",
  "status":"INDEXING"
}
```

---

## Get Repository

```
GET /repositories/{id}
```

Returns:

- Framework
- Language
- DNA Status
- Last Scan
- Health Score

---

## Scan Repository

```
POST /repositories/{id}/scan
```

Triggers a new indexing process.

---

# DNA APIs

## Generate DNA

```
POST /dna/generate
```

Request

```json
{
  "repositoryId":"REP-1001"
}
```

---

## Get DNA

```
GET /dna/{dnaId}
```

Example Response

```json
{
  "dnaId":"DNA-100",
  "businessCapability":"Checkout",
  "framework":"Playwright",
  "reuseScore":97,
  "stability":99.4
}
```

---

## Compare DNA

```
POST /dna/compare
```

Request

```json
{
 "source":"DNA-100",
 "target":"DNA-221"
}
```

Returns

- Similarity
- Shared Components
- Reuse Opportunities

---

# Semantic Search APIs

## Natural Language Search

```
POST /search
```

Example

```json
{
  "query":"Find reusable checkout automation"
}
```

Response

```json
{
 "results":[]
}
```

---

## Similar Tests

```
GET /search/tests
```

Parameters

```
requirementId

dnaId

limit

confidence
```

---

## Search APIs

```
GET /search/apis

GET /search/components

GET /search/pageobjects

GET /search/failures
```

---

# Knowledge Graph APIs

## Graph Traversal

```
GET /graph/traverse
```

Parameters

```
startNode

depth

relationshipType
```

---

## Connected Assets

```
GET /graph/related/{id}
```

Returns

- Requirements
- APIs
- Tests
- Components
- Pipelines

---

## Impact Analysis

```
POST /graph/impact
```

Input

```
Component

Commit

API

Requirement
```

Returns

Affected assets.

---

# AI Copilot APIs

## Ask Copilot

```
POST /copilot/chat
```

Example

```json
{
 "question":"Show reusable login automation"
}
```

Response

```json
{
 "answer":"...",
 "citations":[],
 "confidence":98
}
```

---

## Conversation History

```
GET /copilot/conversations
```

---

## Suggested Questions

```
GET /copilot/suggestions
```

---

# Requirement APIs

## Upload Requirement

```
POST /requirements
```

Supports

- Jira
- Azure DevOps
- Markdown
- PDF

---

## Analyze Requirement

```
POST /requirements/analyze
```

Returns

- Existing Automation
- Coverage
- Reuse Score

---

# Failure Intelligence APIs

## Upload Failure

```
POST /failures
```

Includes

- Stack Trace
- Screenshot
- Video
- DOM
- Logs

---

## Root Cause

```
POST /failures/rootcause
```

Returns

- Classification
- Similar Failures
- Suggested Fix

---

# Execution APIs

## Upload Test Run

```
POST /executions
```

---

## Execution History

```
GET /executions/{testId}
```

---

## Metrics

```
GET /executions/metrics
```

---

# Analytics APIs

```
GET /analytics/dashboard

GET /analytics/reuse

GET /analytics/stability

GET /analytics/coverage

GET /analytics/quality
```

---

# Administration APIs

```
POST /users

POST /roles

POST /permissions

POST /projects

POST /organizations
```

---

# Webhooks

Supported Events

```
Repository Indexed

DNA Generated

Requirement Added

Execution Completed

Failure Detected

Recommendation Created

Graph Updated
```

Example

```json
{
 "event":"DNA_GENERATED",
 "repository":"edge-ui"
}
```

---

# WebSocket APIs

Real-time events

```
DNA Processing

Repository Scan

Execution Progress

Graph Update

Notifications
```

---

# API Security

Supports

- JWT
- OAuth2
- RBAC
- Tenant Isolation
- Rate Limiting
- Audit Logs
- IP Restrictions

---

# Pagination

```
?page=1

&size=25
```

---

# Filtering

```
framework=playwright

language=typescript

risk=critical

reuseScore>90
```

---

# Sorting

```
sort=reuseScore

sort=stability

sort=confidence
```

---

# Rate Limits

| API Type | Limit |
|----------|-------|
| Search | 300/min |
| AI Chat | 60/min |
| DNA | 120/min |
| Graph | 300/min |

---

# API SDKs

Official SDKs

- Python

- TypeScript

- Java

- C#

- Go

Future

- Kotlin

- Rust

---

# CLI

```
testdna login

testdna search

testdna scan

testdna analyze

testdna ask

testdna graph

testdna impact
```

---

# VS Code Extension APIs

```
Search Current Test

Find Similar Tests

Generate DNA

Ask Copilot

Impact Analysis

Failure Explanation
```

---

# MCP Support (Future)

TestDNA-AI will expose MCP-compatible tools allowing AI assistants to safely interact with enterprise testing knowledge.

Example capabilities:

- Search reusable automation
- Retrieve DNA profiles
- Analyze requirements
- Perform impact analysis
- Query the Knowledge Graph
- Explain historical failures

This enables integration with modern AI ecosystems while keeping enterprise data secure and permission-aware.

---

# OpenAPI Support

The platform will publish:

```
/openapi.json
```

and

```
/swagger
```

allowing automatic SDK generation, API exploration, and client integration.

---

# API Lifecycle

```text
Client Request
      │
      ▼
Authentication
      │
      ▼
Authorization
      │
      ▼
Validation
      │
      ▼
Business Service
      │
      ▼
DNA Engine / Graph / Search
      │
      ▼
AI Reasoning (if applicable)
      │
      ▼
Response Builder
      │
      ▼
JSON Response
```

---

# Design Principles

Every API should be:

- Predictable
- Versioned
- Secure
- Observable
- Explainable
- Backward Compatible
- Enterprise Ready
- AI Friendly

---

# Summary

The TestDNA-AI API Platform is designed as the foundation for an extensible AI-native ecosystem.

By exposing every capability through secure, versioned APIs, the platform enables seamless integration with developer tools, CI/CD pipelines, IDEs, enterprise systems, and future AI agents. Whether consumed by a web application, CLI, VS Code extension, or autonomous AI workflow, the APIs provide a consistent, explainable, and scalable interface to the organization's testing knowledge.
